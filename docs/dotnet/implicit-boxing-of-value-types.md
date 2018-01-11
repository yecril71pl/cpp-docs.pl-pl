---
title: "Niejawna konwersja Boxing typów wartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c4725cdd7e8630131f77e02eedc2af14a469d20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implicit-boxing-of-value-types"></a>Niejawna konwersja boxing typów wartości
Konwersja boxing typów wartości zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W projekcie języka możemy nałożone filozoficzne pozycji zamiast praktycznego doświadczenia z funkcją i, w praktyce było błędu. Jako odpowiednio w oryginalnym wielu projektów języka dziedziczenia, Stroustrup decyzję nie można zainicjować obiektu podrzędnego wirtualnej klasy podstawowej w konstruktorze klasy pochodnej, czy w związku z tym język potrzebne dowolnej klasy służy jako wirtualnej podstawy Klasa musi definiować konstruktora domyślnego. Ten konstruktor domyślny, który będzie wywoływany przez wszystkie kolejne pochodnym wirtualnego jest.  
  
 Problem hierarchii wirtualna klasa podstawowa jest, że odpowiedzialny za inicjowanie obiektu podrzędnego wirtualnego współużytkowanego przewiduje z każdego kolejnych pochodnym. Na przykład jeśli można zdefiniować klasę podstawową dla którego zainicjowanie wymaga alokacji buforu, określone przez użytkownika rozmiar buforu tego mogą być przekazywane jako argument do konstruktora. Jeśli dwa kolejne pochodne wirtualnego I udzielić im, połączeń telefonicznych z nimi `inputb` i `outputb`, każdy z nich zapewnia określonej wartości do konstruktora klasy podstawowej. Teraz, kiedy I pochodnych `in_out` klasy z obu `inputb` i `outputb`, żaden z tych wartości do obiektu podrzędnego udostępnionego wirtualna klasa podstawowa rozsądnym były dozwolone do oceny.  
  
 W związku z tym oryginalnego projektu języka Stroustrup niedozwolone Jawne inicjowanie wirtualnej klasy podstawowej w obrębie listy inicjowania elementu członkowskiego konstruktora klasy pochodnej. Gdy to rozwiązuje problem, w praktyce niemożność bezpośrednie inicjowania wirtualna klasa podstawowa niemożliwa. Jan Gorlen National Institute kondycji, który ma zaimplementowany bezpłatnych wersji biblioteki kolekcji SmallTalk, nazywany nihcl, został głosu zasady w przekonujące Stroustrup, który miał korzystać z bardziej elastyczne projektu języka.  
  
 Zasada hierarchiczna obiektowego przechowuje czy klasy pochodnej powinien zajęcie się tylko z implementacji nieprywatne jego natychmiastowego klas podstawowych. Aby zapewnić obsługę projektowania elastyczne inicjowania wirtualnego dziedziczenia, Stroustrup nastąpiło naruszenie tej zasady. Najdalszych pochodnych klas w hierarchii przyjmuje, że dla wszystkich inicjowania obiektu podrzędnego wirtualnego niezależnie od tego, jak głęboko w hierarchii, gdy pojawi się. Na przykład `inputb` i `outputb` są odpowiedzialne za jawnie inicjowanie ich natychmiastowe wirtualnej klasy podstawowej. Gdy `in_out` pochodzi z obu `inputb` i `outputb`, `in_out` staje się odpowiedzialny inicjowania raz usunięte z wirtualnej klasy podstawowej i inicjowania jawnie w `inputb` i `outputb` jest pominięte.  
  
 Zapewnia to elastyczność wymagane przez deweloperów języka, ale kosztem skomplikowane semantyki. To obciążenie complication jest oczyszczony optymalizacji przypadku stosujemy ograniczenia wirtualna klasa podstawowa nie stanu i po prostu zezwolenie na określony interfejs. Jest to idiom zalecany projekt w języku C++. W ramach CLR programowania jest wywoływane zasady do typu interfejsu.  
  
 Oto przykładowy kod proste — i w takim przypadku jawnej konwersji boxing nie jest konieczne:  
  
```  
// Managed Extensions for C++ requires explicit __box operation  
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };  
Object* myObjArray __gc[] = {   
   __box(26), __box(27), __box(28), __box(29), __box(30)  
};  
  
Console::WriteLine( "{0}\t{1}\t{2}", __box(0),  
   __box(my1DIntArray->GetLowerBound(0)),  
   __box(my1DIntArray->GetUpperBound(0)) );  
```  
  
 Jak widać, istnieje wiele pakującej przejściem. W programie Visual C++, typ wartości jest niejawnej konwersji boxing:  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [OPAKOWYWANIE](../windows/boxing-cpp-component-extensions.md)