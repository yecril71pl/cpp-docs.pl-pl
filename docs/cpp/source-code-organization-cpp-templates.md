---
title: Organizacja kodu źródłowego (szablony języka C++)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 1933758e47f2fcc0b63f0d16809591b932501854
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611392"
---
# <a name="source-code-organization-c-templates"></a>Organizacja kodu źródłowego (szablony języka C++)

Podczas definiowania szablonu klasy, należy zorganizować kodu źródłowego w taki sposób, że definicje elementów członkowskich są widoczne w kompilatorze, kiedy ich potrzebuje.   Masz do wyboru używania *modelu włączenia* lub *jawne utworzenie wystąpienia* modelu. W modelu dołączania możesz uwzględnić definicje elementów członkowskich w każdym pliku, który używa szablonu. To podejście jest najprostsza i zapewnia maksymalną elastyczność pod względem typów konkretnych mogą być używane z szablonu. Jego wadą jest to zwiększyć czas kompilacji. Wpływ może być istotne, jeśli projekt i/lub same pliki dołączone są duże. W przypadku jawnego utworzenia wystąpienia metody samego szablonu tworzy konkretnych klas lub składowych klasy dla określonych typów.  Takie podejście może przyspieszyć czasy kompilacji, ale ogranicza użycie do tych klas, które implementujący szablon ma włączone wcześniej. Ogólnie rzecz biorąc zaleca się użycie modelu dołączania, chyba że czasy kompilacji stać się problemem.

## <a name="background"></a>Tło

Szablony nie są takie jak zwykłej klasy, w tym sensie, że kompilator nie generuje kod obiektowy dla szablonu lub dowolny z jej członków. Nie ma nic do generowania, dopóki nie zostanie utworzone wystąpienie szablonu przy użyciu typów konkretnych. Gdy kompilator napotka konkretyzacji szablonu takich jak `MyClass<int> mc;` i klasy z ten podpis istnieje jeszcze, generuje nową klasę. Ponadto próbuje wygenerować kod dla dowolnej funkcji elementów członkowskich, które są używane. Jeśli te definicje znajdują się w pliku, który nie jest #included, bezpośrednio lub pośrednio w pliku .cpp, który jest kompilowany, kompilator nie widzi.  Z punktu widzenia kompilatora to niekoniecznie błąd, ponieważ funkcje mogą być zdefiniowane w innej jednostce translacji, w których przypadku konsolidator będzie je znaleźć.  Jeśli konsolidator nie może znaleźć kod, uruchamia **nierozpoznany zewnętrzny** błędu.

## <a name="the-inclusion-model"></a>Model dołączania

Najprostszy i najbardziej powszechnym sposobem widoczności w całej jednostki translacji, definicje szablonów jest umieścić definicje w samym pliku nagłówka.  Dowolny plik .cpp, która używa tego szablonu, ale po prostu ma # include. To podejście użyte w standardowej bibliotece.

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

W przypadku tej metody kompilator ma dostęp do definicji kompletny szablon oraz można utworzyć wystąpienie szablony na żądanie dla dowolnego typu. Jest proste i stosunkowo łatwa w obsłudze. Jednak model włączenia kosztują pod względem czasy kompilacji.   Ten koszt może być istotne w przypadku dużych programów, zwłaszcza wtedy, gdy sam nagłówek szablonu #includes innych nagłówków. Pliki .cpp, każdy z #includes nagłówek otrzyma własną kopię szablony funkcji i wszystkich definicji. Konsolidator zazwyczaj będzie można posortować elementy tak, aby nie kończą z wieloma definicjami dla funkcji, ale zajmuje trochę czasu, aby wykonać to zadanie. Mniejszymi programami, że czas kompilacji dodatkowe, prawdopodobnie nie ma znaczenia.

## <a name="the-explicit-instantiation-model"></a>Model jawne Tworzenie wystąpienia

Jeśli model dołączania nie jest wygodną dla projektu, a ostatecznie znasz zestaw typów, które będą używane do utworzenia wystąpienia szablonu, można rozdzielić kod szablonu do pliku .h i .cpp i w pliku .cpp jawnie utworzyć wystąpienie szablonów. Spowoduje to generowania kodu obiektu kompilator zostanie wyświetlony, gdy wystąpi wystąpień użytkownika.

Jawne tworzenie wystąpienia możesz utworzyć przy użyciu szablonu — słowo kluczowe, następuje podpis jednostka, do której chcesz utworzyć wystąpienie. Może to być typu lub elementu członkowskiego. Jeśli jawnie utworzyć wystąpienia typu, wszystkie elementy członkowskie są tworzone.

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
    for(const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

W poprzednim przykładzie jawne utworzenie wystąpień są w dolnej części pliku .cpp. A `MyArray` mogą być używane tylko w przypadku **double** lub `String` typów.

> [!NOTE]
> W języku C ++ 11 **wyeksportować** — słowo kluczowe została zakończona w kontekście definicji szablonu. W praktyce ma little wpływ ponieważ nigdy nie obsługuje większość kompilatorów.