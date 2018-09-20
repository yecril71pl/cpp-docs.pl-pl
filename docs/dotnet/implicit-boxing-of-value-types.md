---
title: Niejawna konwersja Boxing typów wartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387591"
---
# <a name="implicit-boxing-of-value-types"></a>Niejawna konwersja boxing typów wartości

Konwersja boxing typów wartości zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

W projekcie języka możemy nałożone filozoficzne pozycji audytów praktyczne doświadczenie z funkcją, i w praktyce było błędu. Jako odpowiednio w oryginalnym wielu projektów języka dziedziczenia, Stroustrupa decyzję, nie można zainicjować obiektu podrzędnego wirtualnej klasy bazowej w konstruktorze klasy pochodnej, i dlatego języka wymagane, dowolnej klasy służącej jako baza wirtualna Klasa należy zdefiniować Konstruktor domyślny. To tego domyślnego konstruktora, który będzie wywoływany przez wszystkie kolejne dziedziczenia wirtualnego.

Problem hierarchii wirtualnej klasy bazowej polega na tym, że odpowiedzialność za inicjowanie obiektu współużytkowanego podrzędnych wirtualnych przenosi się z każdej kolejnej pochodnym. Na przykład jeśli zdefiniować klasę bazową dla inicjowania, które wymaga alokacji buforu, rozmiar tego buforu określonego przez użytkownika mogą być przekazywane jako argumentu do konstruktora. Jeśli następnie podać dwa kolejne pochodnymi wirtualnych, ich wywoływania `inputb` i `outputb`, każdy z nich zapewnia określoną wartość do konstruktora klasy bazowej. Teraz, kiedy I pochodne `in_out` klasy z obu `inputb` i `outputb`, żadna z tych wartości do obiektu podrzędnego udostępnionego wirtualnej klasy bazowej można rozsądnym mieć możliwość oceny.

W związku z tym oryginalnym projekcie języka Stroustrupa niedozwolone Jawne inicjowanie wirtualnej klasy bazowej, w ramach elementu członkowskiego listy inicjowania konstruktora klasy pochodnej. Gdy to rozwiązuje problem, w praktyce z brakiem, aby kierować inicjowania wirtualnej klasy bazowej niemożliwa. Keith Gorlen National Institute of zdrowia, który ma zaimplementowany bezpłatną wersję biblioteki kolekcji SmallTalk o nazwie nihcl, był głosu zasady w przekonujące Stroustrupa, he 'D, co pozwoli uzyskać bardziej elastyczne projektowanie języków.

Zasada hierarchiczne programowania obiektowego przechowuje czy klasę pochodną powinna dotyczyć samej tylko w przypadku implementacji nieprywatny jego natychmiastowego klas bazowych. Aby włączyć obsługę projektowania elastyczne inicjowanie dla dziedziczenia wirtualnego, Stroustrupa musiał naruszenie tej zasady. Najbardziej pochodnej klasy w hierarchii przyjmuje odpowiedzialność za wszystkie inicjowania obiektu podrzędnego wirtualnego niezależnie od tego, jak głęboko do hierarchii, gdy pojawi się. Na przykład `inputb` i `outputb` są odpowiedzialne za jawne inicjowanie ich natychmiastowy wirtualnej klasy bazowej. Gdy `in_out` pochodzi z obu `inputb` i `outputb`, `in_out` staje się odpowiada inicjowania raz usunięte z wirtualnej klasy bazowej i Inicjowanie jawnie w ramach `inputb` i `outputb` jest pominięte.

Zapewnia to elastyczność, wymagane przez deweloperów języka, ale kosztem semantyki skomplikowane. Ten ciężar kompilacji jest usuwany natychmiast, jeśli będziemy ograniczać przydziału obowiązków wirtualnej klasy bazowej nie stanie, i po prostu zezwalała na określony interfejs. Jest to idiom zalecany projekt w języku C++. W ramach CLR programowania jest zgłaszany do zasad z typem interfejsu.

Oto przykład prostego kodu — a w tym przypadku jawne pakowanie nie jest konieczne:

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

Jak widać, istnieje wiele pakowania dzieje. W obszarze Visual C++, typ wartości opakowywanie to niejawna:

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>Zobacz też

[Typy wartości i ich zachowania (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Konwersja boxing](../windows/boxing-cpp-component-extensions.md)