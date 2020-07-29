---
title: Zasady ogólne dotyczące przeciążania operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: da0bf04435118c819fc29efd3082d8d312e43006
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213401"
---
# <a name="general-rules-for-operator-overloading"></a>Zasady ogólne dotyczące przeciążania operatorów

Następujące reguły ograniczają sposób implementacji przeciążonych operatorów. Jednak nie mają zastosowania do operatorów [New](../cpp/new-operator-cpp.md) i [delete](../cpp/delete-operator-cpp.md) , które są objęte odrębnie.

- Nie można definiować nowych operatorów, takich jak **.**.

- Nie można ponownie zdefiniować znaczenia operatorów po zastosowaniu wbudowanych typów danych.

- Przeciążone operatory muszą być niestatyczną funkcją składową klasy lub funkcją globalną. Funkcja globalna, która wymaga dostępu do prywatnych lub chronionych składowych, klasy musi być zadeklarowana jako zaprzyjaźniona z tą klasą. Funkcja globalna musi mieć przynajmniej jeden argument klasy lub typu wyliczeniowego lub odwołanie do klasy lub typu wyliczeniowego. Na przykład:

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

   Poprzedni przykład kodu deklaruje operator „mniejszy niż” jako funkcję członkowską; jednakże operatory dodawania są zadeklarowane jako funkcje globalne, które mają dostęp zaprzyjaźniony. Należy zauważyć, że więcej niż jedna implementacja może być dostarczona dla danego operatora. W przypadku poprzedniego operatora dodawania, dwie implementacje są dostarczane w celu ułatwienia przemienności. Jest tak samo, jak najprawdopodobniej, że operatory, które dodają `Point` do, `Point` **`int`** do `Point` , i tak dalej, mogą zostać zaimplementowane.

- Operatory przestrzegają zasad pierwszeństwa, grupowania i liczby operandów podyktowanej ich typowym zastosowaniem w typach wbudowanych. W związku z tym nie istnieje sposób wyrażenia koncepcji "Dodaj 2 i 3 do obiektu typu `Point` ", oczekiwano 2 do dodania do współrzędnej *x* i 3, aby dodać do współrzędnych *y* .

- Operatory jednoargumentowe deklarowane jako funkcje członkowskie nie przyjmują argumentów; jeśli są zadeklarowane jako funkcje globalne, przyjmują jeden argument.

- Operatory binarne deklarowane jako funkcje członkowskie przyjmują jeden argument; jeśli są zadeklarowane jako funkcje globalne, przyjmują dwa argumenty.

- Jeśli operator może być używany jako operator jednoargumentowy lub binarny ( __&__ , __*__ , __+__ i __-__ ), można przeciążać każde użycie osobno.

- Przeciążone operatory nie mogą mieć argumentów domyślnych.

- Wszystkie przeciążone operatory poza przypisaniem (**operator =**) są dziedziczone przez klasy pochodne.

- Pierwszy argument dla przeciążonego operatora funkcji składowej jest zawsze typem klasy obiektu, dla którego operator jest wywoływany (klasy, w której operator jest zadeklarowany lub klasa pochodnej dla tej klasy). Konwersje nie są dostarczane dla pierwszego argumentu.

Należy zauważyć, że znaczenie któregokolwiek z operatorów może być całkowicie zmienione. Obejmuje to znaczenie operatorów address-of ( **&** ), przypisania ( **=** ) i wywołania funkcji. Tożsamości, które mogą być powoływane dla wbudowanych typów, mogą być zmienione za pomocą przeciążenia operatora. Na przykład, poniższe cztery instrukcje są zazwyczaj równoważne po całkowitym obliczeniu:

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

Ta tożsamość nie może polegać na typach klasy, które przeciążają operatory. Ponadto, niektóre wymagania niejawne w korzystaniu z tych operatorów dla typów podstawowych są złagodzone dla operatorów przeciążonych. Na przykład operator dodawania/przypisywania, **+=** wymaga, aby lewy argument operacji był wartością l, w przypadku zastosowania do typów podstawowych; nie ma takiego wymagania, gdy operator jest przeciążony.

> [!NOTE]
> Aby zapewnić spójność, najlepiej posługiwać się modelem typów wbudowanych podczas definiowania operatorów przeciążonych. Jeżeli semantyka operatorów przeciążonych różni się znacznie od ich znaczenia w innych kontekstach, może być to bardziej skomplikowane niż użyteczne.

## <a name="see-also"></a>Zobacz także

[Przeciążanie operatora](../cpp/operator-overloading.md)
