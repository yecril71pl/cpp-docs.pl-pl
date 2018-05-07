---
title: Interfejsy (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6be3b207f6bd64685f7ec1d3f6d2271ec3b83f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interfaces-ccx"></a>Interfejsy (C + +/ CX)
Chociaż klasa ref może dziedziczyć co najwyżej jedną konkretną klasę podstawową, on implementować dowolną liczbę interfejsu klasy. Klasa interfejsu (lub struktury interfejsu) siebie może dziedziczyć (lub wymagają) wielu interfejsu klasy, można przeciążyć funkcji jego elementów członkowskich i może mieć parametrów typu.  
  
## <a name="characteristics"></a>Właściwości  
 Interfejs ma następujące cechy:  
  
-   Klasa interfejsu (lub struct) musi być zadeklarowana w przestrzeni nazw i może mieć dostępności publicznych lub prywatnych. Tylko publiczne interfejsy są emitowane metadanych.  
  
-   Elementy członkowskie interfejsu może zawierać właściwości, metod i zdarzeń.  
  
-   Wszystkie elementy członkowskie interfejsu są niejawnie publicznego i wirtualnych.  
  
-   Pola i statyczne elementy członkowskie nie są dozwolone.  
  
-   Typy, które są używane jako parametry metody, właściwości ani zwracać wartości można tylko typów środowiska wykonawczego systemu Windows. w tym typy podstawowe i typy wyliczeniowe klasy.  
  
## <a name="declaration-and-usage"></a>Deklaracja i użycia  
 Poniższy przykład pokazuje, jak można zadeklarować interfejsu. Zwróć uwagę, że interfejs mogą być deklarowane jako typ klasy lub struktury.  
  
 [!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]  
  
 Aby zaimplementować interfejs, klasy referencyjnej lub ref struct deklaruje i implementuje właściwości i metod wirtualnych. Interfejs i implementującej klasy ref muszą używać takie same nazwy parametrów metody, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]  
  
## <a name="interface-inheritance-hierarchies"></a>Interfejs hierarchii dziedziczenia  
 Interfejs może dziedziczyć z jednego lub więcej interfejsów. Jednak w przeciwieństwie do klasy referencyjnej lub struktury, interfejsu nie deklaruj elementów członkowskich dziedziczony interfejs. Jeśli interfejs B dziedziczy interfejs A, a klasa ref C dziedziczy B, C musi implementować zarówno A, jak i B. Przedstawiono to w następnym przykładzie.  
  
 [!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]  
  
## <a name="implementing-interface-properties-and-events"></a>Implementacja interfejsu właściwości i zdarzenia  
 Jak pokazano w poprzednim przykładzie, można użyć prostej właściwości wirtualnych do zaimplementowania właściwości interfejsu. Można też podać ustawiających implementującej klasy i metody pobierające niestandardowych.  Metody pobierającej i ustawiającej muszą być publiczne we właściwości interfejsu.  
  
 [!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]  
  
 Jeśli interfejs deklaruje właściwość tylko do pobrania lub w trybie tylko do zestawu, klasy implementującej powinien dostarczyć jawnie metody pobierającej lub ustawiającej.  
  
 [!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]  
  
 Można też wdrożyć niestandardowe Dodawanie i usuwanie metody zdarzenia w klasie implementującej.  
  
## <a name="explicit-interface-implementation"></a>Jawna implementacja interfejsu  
 Gdy klasa ref implementuje wiele interfejsów i te interfejsy mają metody, których nazwy i podpisy są identyczne w kompilatorze, służy następującej składni Aby jawnie wskazać metody interfejsu, który implementuje metody klasy.  
  
 [!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 W języku C + +/ CX, `generic` — słowo kluczowe jest używana do reprezentowania typu sparametryzowana środowiska wykonawczego systemu Windows. Sparametryzowany typ jest emitowany w metadanych i mogą być używane przez kod, który jest zapisany w dowolnym języku obsługująca parametrów typu. Niektórych interfejsach definiuje środowiska uruchomieniowego systemu Windows — na przykład [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)—, ale go nie obsługuje tworzenia publiczne interfejsy ogólne zdefiniowane przez użytkownika w języku C + +/ CX. Można jednak utworzyć prywatnego interfejsach.  
  
 Oto, jak typów środowiska wykonawczego systemu Windows może służyć do tworzenia interfejs generyczny:  
  
-   Element ogólny zdefiniowane przez użytkownika `interface class` w składnika nie może być wydane do jego pliku metadanych systemu Windows; w związku z tym nie może mieć publicznych ułatwień dostępu i kod klienta w innych plików winmd nie może go zaimplementować. Może być implementowana przez klasy ref niepublicznych w tym samym składnikiem. Klasa ref publicznych może mieć interfejs ogólny typ jako członek prywatny.  
  
     Poniższy fragment kodu przedstawia sposób zadeklarować ogólnego `interface class` ją wdrożyć w prywatnej klasy ref i klasa ref służy jako członek prywatny w klasie ref publicznego.  
  
     [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]  
  
-   Interfejs ogólny wykonaj zasady standardowy interfejs ułatwień dostępu, elementy członkowskie, *wymaga* relacje, klasy podstawowej i tak dalej.  
  
-   Interfejs ogólny może potrwać co najmniej jeden parametr typu ogólnego, poprzedzone `typename` lub `class`. Parametry bez typu nie są obsługiwane.  
  
-   Parametr typu mogą być dowolnego typu środowiska wykonawczego systemu Windows. Oznacza to, że parametr typu może być typu odwołania, typu wartości, klasy interfejsu, delegata, podstawowe typu lub klasy publicznym typie wyliczeniowym.  
  
-   A *zamknięte ogólny interfejs* jest interfejsem dziedziczy interfejs ogólny, który określa argumenty typu konkretnego dla wszystkich parametrów typu. Umożliwia dowolnym można nieogólnego interfejsu prywatnego.  
  
-   *Otwórz interfejs ogólny* jest interfejs, który ma co najmniej jeden parametr typu, dla których nie konkretnego typu jest jeszcze dostępne. Umożliwia dowolnym że typu mogą być używane, tym jako argument typu inny interfejs generyczny.  
  
-   Można parametryzacja tylko cały interfejs, nie poszczególnych metod.  
  
-   Parametry typu nie może być ograniczony.  
  
-   Zamknięte ogólny interfejs ma niejawnie wygenerowany identyfikator UUID. Użytkownik nie może określić identyfikator UUID.  
  
-   W interfejsie, wszystkie odwołania do bieżącego interfejsu — w parametr metody zwracać wartość lub właściwość — przyjęto, że do odwoływania się do bieżącego wystąpienia. Na przykład *IMyIntf* oznacza *IMyIntf\<T >*.  
  
-   Typ parametru metody po parametrze typu deklaracji parametr lub zmienna, użyta zostanie nazwa parametru typu bez wskaźnika, odwołanie do natywnego lub deklaratorów dojścia. Innymi słowy, nigdy nie zapisu "T ^".  
  
-   Klasy ref opartego na szablonie muszą być prywatne. Można zaimplementować interfejsów ogólnych i może przekazać parametr szablonu *T* do argumentów ogólnych *T*. Każdego wystąpienia klasy ref opartego na szablonie jest klasa ref.  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)