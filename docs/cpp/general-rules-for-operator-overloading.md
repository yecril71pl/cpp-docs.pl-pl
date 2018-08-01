---
title: Zasady ogólne dotyczące przeciążania operatorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80058aa22de10088c3901d0c129635288bf880b5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403459"
---
# <a name="general-rules-for-operator-overloading"></a>Zasady ogólne dotyczące przeciążania operatorów
Następujące reguły ograniczają sposób implementacji przeciążonych operatorów. Jednak nie mają zastosowania do [nowe](../cpp/new-operator-cpp.md) i [Usuń](../cpp/delete-operator-cpp.md) operatorów, które zostały omówione oddzielnie.  
  
-   Nie można definiować nowych operatorów, takich jak **.**.  
  
-   Nie można ponownie zdefiniować znaczenia operatorów po zastosowaniu wbudowanych typów danych.  
  
-   Przeciążone operatory muszą być niestatyczną funkcją składową klasy lub funkcją globalną. Funkcja globalna, która wymaga dostępu do prywatnych lub chronionych składowych, klasy musi być zadeklarowana jako zaprzyjaźniona z tą klasą. Funkcja globalna musi mieć przynajmniej jeden argument klasy lub typu wyliczeniowego lub odwołanie do klasy lub typu wyliczeniowego. Na przykład:  
  
    ```cpp  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     Poprzedni przykład kodu deklaruje operator „mniejszy niż” jako funkcję członkowską; jednakże operatory dodawania są zadeklarowane jako funkcje globalne, które mają dostęp zaprzyjaźniony. Należy zauważyć, że więcej niż jedna implementacja może być dostarczona dla danego operatora. W przypadku poprzedniego operatora dodawania, dwie implementacje są dostarczane w celu ułatwienia przemienności. Jest po prostu jako prawdopodobnie tego operatory, które dodają `Point` do `Point`, **int** do `Point`i tak dalej, mogą zostać zaimplementowane.  
  
-   Operatory przestrzegają zasad pierwszeństwa, grupowania i liczby operandów podyktowanej ich typowym zastosowaniem w typach wbudowanych. W związku z tym, nie istnieje żaden sposób, aby zapisać koncepcję "dodanie 2 i 3 do obiektu typu `Point`," Oczekiwano 2, które mają zostać dodane do *x* współrzędnych i 3, które mają zostać dodane do *y* koordynacji.  
  
-   Operatory jednoargumentowe deklarowane jako funkcje członkowskie nie przyjmują argumentów; jeśli są zadeklarowane jako funkcje globalne, przyjmują jeden argument.  
  
-   Operatory binarne deklarowane jako funkcje członkowskie przyjmują jeden argument; jeśli są zadeklarowane jako funkcje globalne, przyjmują dwa argumenty.  
  
-   Jeśli operator może służyć jako jednoargumentowy lub binarny (__&__, __*__, __+__, i __-__), może doprowadzić do przeciążenia każdego zastosowania oddzielnie.  
  
-   Przeciążone operatory nie mogą mieć argumentów domyślnych.  
  
-   Wszystkie przeciążone operatory z wyjątkiem przypisania (**operator =**) są dziedziczone przez klasy pochodne.  
  
-   Pierwszy argument dla przeciążonego operatora funkcji składowej jest zawsze typem klasy obiektu, dla którego operator jest wywoływany (klasy, w której operator jest zadeklarowany lub klasa pochodnej dla tej klasy). Konwersje nie są dostarczane dla pierwszego argumentu.  
  
 Należy zauważyć, że znaczenie któregokolwiek z operatorów może być całkowicie zmienione. Który uwzględnia znaczenie address-of (**&**), przypisanie (**=**) i operatory wywołania funkcji. Tożsamości, które mogą być powoływane dla wbudowanych typów, mogą być zmienione za pomocą przeciążenia operatora. Na przykład, poniższe cztery instrukcje są zazwyczaj równoważne po całkowitym obliczeniu:  
  
```cpp 
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 Ta tożsamość nie może polegać na typach klasy, które przeciążają operatory. Ponadto, niektóre wymagania niejawne w korzystaniu z tych operatorów dla typów podstawowych są złagodzone dla operatorów przeciążonych. Na przykład operator dodawania/przypisania **+=**, wymaga lewy operand miał l wartością po zastosowaniu do podstawowych typów; nie jest takie wymagany, gdy operator jest przeciążony.  
  
> [!NOTE]
> Aby zapewnić spójność, najlepiej posługiwać się modelem typów wbudowanych podczas definiowania operatorów przeciążonych. Jeżeli semantyka operatorów przeciążonych różni się znacznie od ich znaczenia w innych kontekstach, może być to bardziej skomplikowane niż użyteczne.  
  
## <a name="see-also"></a>Zobacz także  
 [Przeładowanie operatora](../cpp/operator-overloading.md)