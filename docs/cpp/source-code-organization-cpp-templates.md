---
title: Organizacja kodu źródłowego (szablony C++)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: ecd682056f27200ae31c27295c1aabaf72c74a18
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186116"
---
# <a name="source-code-organization-c-templates"></a>Organizacja kodu źródłowego (szablony C++)

Podczas definiowania szablonu klasy należy zorganizować kod źródłowy w taki sposób, aby definicje elementów członkowskich były widoczne dla kompilatora, gdy ich potrzebują. Możesz wybrać *model dołączania* lub *jawny model tworzenia wystąpienia* . W modelu dołączania można uwzględnić definicje elementów członkowskich w każdym pliku, który używa szablonu. Ta metoda jest najprostsza i zapewnia maksymalną elastyczność w zakresie tego, jakie konkretne typy mogą być używane z szablonem. Wadą jest to, że może to wydłużyć czas kompilacji. Wpływ może być znaczący, jeśli projekt i/lub dołączone pliki są duże. W przypadku jawnego podejścia tworzenia wystąpienia, sam szablon tworzy wystąpienia konkretnych klas lub elementów członkowskich klasy dla określonych typów.  Takie podejście może przyspieszyć kompilację, ale ogranicza użycie wyłącznie do tych klas, które implementują szablon. Ogólnie rzecz biorąc, zalecamy użycie modelu dołączania, chyba że czasy kompilacji staną się problemem.

## <a name="background"></a>Tło

Szablony nie są podobne do zwykłych klas w sensie, że kompilator nie generuje kodu obiektu dla szablonu lub któregokolwiek z jego składowych. Nie ma nic do wygenerowania do momentu wystąpienia szablonu z konkretnymi typami. Gdy kompilator napotyka wystąpienia szablonu, takie jak `MyClass<int> mc;` i nie istnieje jeszcze Klasa o tej sygnaturze, generuje nową klasę. Próbuje również wygenerować kod dla wszystkich używanych funkcji składowych. Jeśli te definicje znajdują się w pliku, który nie jest #included, bezpośrednio lub pośrednio, w pliku. cpp, który jest kompilowany, kompilator nie może ich zobaczyć.  Z punktu widzenia kompilatora nie jest to konieczne, ponieważ funkcje mogą być zdefiniowane w innej jednostce tłumaczenia, w takim przypadku konsolidator znajdzie je.  Jeśli konsolidator nie znajdzie tego kodu, wywołuje *nierozpoznany błąd zewnętrzny* .

## <a name="the-inclusion-model"></a>Model dołączania

Najprostszym i najbardziej typowym sposobem, aby definicje szablonów były widoczne w jednostce translacji, jest umieszczenie definicji w samym pliku nagłówkowym.  Każdy plik. cpp, który używa szablonu, po prostu ma #include nagłówku. Jest to podejście używane w standardowej bibliotece.

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   }
};
#endif
```

W tym podejściu kompilator ma dostęp do kompletnej definicji szablonu i może tworzyć wystąpienia szablonów na żądanie dla dowolnego typu. Jest to proste i stosunkowo łatwe w obsłudze. Jednak model dołączania ma koszt w odniesieniu do czasu kompilacji. Ten koszt może być znaczny w dużych programach, szczególnie jeśli sam nagłówek szablonu #includes inne nagłówki. Każdy *`.cpp`* plik, który #includes nagłówku, otrzyma własną kopię szablonów funkcji i wszystkie definicje. Konsolidator będzie zazwyczaj mógł posortować elementy w taki sposób, aby nie można było wykonać wielu definicji dla funkcji, ale konieczne jest wykonanie tej czynności. W mniejszych programach czas trwania dodatkowej kompilacji prawdopodobnie nie jest znaczący.

## <a name="the-explicit-instantiation-model"></a>Jawny model tworzenia wystąpienia

Jeśli model dołączania nie jest żywotny dla Twojego projektu i chcesz uzyskać ostateczny zestaw typów, które będą używane do tworzenia wystąpienia szablonu, można oddzielić kod szablonu do *`.h`* *`.cpp`* pliku i, a następnie w *`.cpp`* pliku jawnie utworzyć wystąpienia szablonów. Spowoduje to wygenerowanie kodu obiektu, który będzie wyświetlany w kompilatorze po napotkaniu wystąpień użytkownika.

Można utworzyć jawne utworzenie wystąpienia przy użyciu szablonu słowa kluczowego, po którym następuje podpis jednostki, którą chcesz utworzyć. Może to być typ lub element członkowski. Jeśli jawnie utworzysz wystąpienie typu, zostaną utworzone wszystkie elementy członkowskie.

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for (const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

W poprzednim przykładzie jawne wystąpienia są w dolnej części pliku. cpp. `MyArray`Może być używany tylko dla **`double`** lub `String` typów.

> [!NOTE]
> W języku C++ 11 **`export`** słowo kluczowe było przestarzałe w kontekście definicji szablonu. W praktyce mają niewielki wpływ, ponieważ większość kompilatorów nigdy nie obsługuje.
