---
title: Źródła kodu organizacji (szablonów języka C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
caps.latest.revision: 5
manager: ghogen
ms.openlocfilehash: 1b3b17c17bad3834774f747548dda6710e178cb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="source-code-organization-c-templates"></a>Organizacja kodu źródłowego (szablonów języka C++)

Podczas definiowania szablonu klasy, Zorganizuj kodu źródłowego w taki sposób, że definicji elementu członkowskiego są widoczne w kompilatorze, podczas musi je.   Masz do dyspozycji *modelu włączenia* lub *jawne utworzenie wystąpienia* modelu. W modelu dołączania możesz dołączyć definicji elementu członkowskiego w każdym pliku, który używa szablonu. Takie podejście jest najprostsza i zapewnia maksymalną elastyczność pod względem konkretne typy mogą być używane z szablonu. Jego wadą jest to, że można zwiększyć czas kompilacji. Wpływ może być istotne, jeśli projekt i/lub same pliki uwzględniane są duże. Z podejścia jawne utworzenie wystąpienia szablonu tworzy konkretnych klas lub członków klasy dla określonych typów.  Tej metody można skrócić czas kompilacji, lecz ogranicza użycie tylko tych klas, które implementujący szablonu włączył wcześniejsze. Ogólnie rzecz biorąc zalecane jest użycie modelu dołączania, chyba że w czasie kompilacji stać się problemem.  
  
## <a name="background"></a>Tło

 Szablony nie są takie jak zwykłe klas w tym sensie, że kompilator nie generuje kod obiektu dla szablonu lub dowolny z jego elementów członkowskich. Nie ma nic do generowania aż do szablonu zostanie uruchomiony z typów konkretnych. Gdy kompilator napotka wystąpienia szablonu takich jak `MyClass<int> mc;` i nie podpisem, że istnieje klasa jeszcze, generuje nową klasę. Ponadto próbuje wygenerować kod dla dowolnej funkcji elementów członkowskich, które są używane. Jeśli te definicje znajdują się w pliku, który nie jest #included, bezpośrednio lub pośrednio w pliku .cpp, który jest kompilowany, kompilator nie są one widoczne.  Z punktu widzenia przez kompilator nie jest to zawsze błąd ponieważ funkcje mogą być zdefiniowane w innej jednostce tłumaczenia, w których przypadku konsolidator będzie je znaleźć.  Jeśli konsolidator nie może znaleźć ten kod, zgłasza **nierozpoznany zewnętrzny** błędu.  

## <a name="the-inclusion-model"></a>Model dołączania

 Najprostszym i najbardziej typowych sposobem uwidaczniania definicje szablonów w jednostce tłumaczenia, jest umieścić definicje w samym pliku nagłówka.  Po prostu ma każdego pliku .cpp, który używa szablonu # include. Jest to metoda używanych w standardowej bibliotece.  
  
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
  
 Takie podejście kompilator ma dostęp do definicji szablonu ukończone i można utworzyć wystąpienia szablony na żądanie dla dowolnego typu. To proste i stosunkowo łatwa do zachowania. Jednak model włączenia ma koszt pod względem czasu kompilacji.   Ten koszt może być istotne w przypadku dużych programów, zwłaszcza, jeśli nagłówek szablonu #includes innych nagłówków. Plik .cpp co #includes nagłówka otrzyma własną kopię szablonów funkcji i wszystkich definicji. Konsolidator zazwyczaj będzie przystąpić czynności, aby nie na końcu wiele definicji dla funkcji, ale czas pracy tego. Mniejszymi programami, że czas dodatkowe kompilacji, prawdopodobnie nie ma znaczenia.  
  
## <a name="the-explicit-instantiation-model"></a>Jawne tworzenie wystąpienia modelu

 Jeśli model włączenia nie jest mogą zostać wykorzystane do projektu, a ostatecznie znasz zestaw typów, które będą używane do utworzenia wystąpienia szablonu, można rozdzielać kod szablonu do pliku .h i .cpp i w pliku .cpp jawnie utworzyć wystąpienia szablonów. To spowoduje, że będzie generowany kod obiektu kompilator zostanie wyświetlony, gdy wykryje wystąpień użytkownika.  
  
 Jawne tworzenie wystąpienia możesz utworzyć za pomocą szablonu — słowo kluczowe następuje podpis obiekt, do którego chcesz utworzyć wystąpienia. Może to być typ lub element członkowski. Jeśli jawnie utworzyć wystąpienia typu są wystąpienia wszystkich elementów członkowskich.  
  
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
#include "stdafx.h"  
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
  
 W poprzednim przykładzie jawne utworzenie wystąpień są w dolnej części pliku .cpp. A `MyArray` mogą być używane tylko do **podwójne** lub **ciąg** typów.  
  
> [!NOTE]
>  W języku C ++ 11 **wyeksportować** — słowo kluczowe została uznana za przestarzałą w kontekście definicji szablonu. W praktyce ma mały wpływ ponieważ nigdy nie obsługuje większość kompilatory.
