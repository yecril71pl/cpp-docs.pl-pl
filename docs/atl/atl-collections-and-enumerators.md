---
title: Kolekcje i wyliczenia ALT
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491902"
---
# <a name="atl-collections-and-enumerators"></a>Kolekcje i wyliczenia ALT

A `collection` jest obiektem com, który udostępnia interfejs, który umożliwia dostęp do grupy elementów danych (nieprzetworzone dane lub inne obiekty). Interfejs, który następuje po standardach zapewniających dostęp do grupy obiektów jest znany jako *interfejs kolekcji*.

Co najmniej interfejsy kolekcji muszą dostarczać `Count` Właściwość zwracającą liczbę elementów w kolekcji `Item` , właściwość zwracająca element z kolekcji na podstawie indeksu i `_NewEnum` Właściwość zwracająca moduł wyliczający dla kolekcji. Opcjonalnie interfejsy kolekcji mogą zapewnić `Add` i `Remove` metody zezwalające na wstawianie elementów do kolekcji lub usuwanie `Clear` ich z niej oraz metodę usuwania wszystkich elementów.

`enumerator` Jest obiektem com, który zapewnia interfejs do iterowania za pomocą elementów w kolekcji. Interfejsy modułu wyliczającego zapewniają dostęp szeregowy do elementów kolekcji za pomocą czterech wymaganych `Next`metod `Skip`: `Reset`,, `Clone`, i.

Więcej informacji na temat interfejsów modułu wyliczającego można uzyskać, odczytując zawartość referencyjną, taką jak interfejs [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

## <a name="in-this-section"></a>W tej sekcji

[Klasy kolekcji i wyliczeń ATL](../atl/atl-collection-and-enumerator-classes.md)<br/>
Krótko opisuje i oferuje linki do klas ATL, które ułatwią implementowanie kolekcji i modułów wyliczających.

[Zasady projektowania interfejsów kolekcji i wyliczeń](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Omawia różne zasady projektowania za każdym typem interfejsu.

[Implementowanie kolekcji opartej na standardowej bibliotece C++](../atl/implementing-an-stl-based-collection.md)<br/>
Rozszerzony przykład, który przeprowadzi Cię przez implementację C++ standardowej kolekcji opartej na bibliotece.

## <a name="related-sections"></a>Sekcje pokrewne

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów koncepcyjnych dotyczących sposobu programowania przy użyciu Active Template Library.

[Przykład ATLCollections](../overview/visual-cpp-samples.md)<br/>
Przykład demonstrujący używanie `ICollectionOnSTLImpl` i `CComEnumOnSTL`i implementacji niestandardowych klas zasad kopiowania.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)
