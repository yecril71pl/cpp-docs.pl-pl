---
title: Klasy kolekcji ATL i wyliczeń
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: a0d7483cc142377ec4de903e27f23056a9e8dd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495309"
---
# <a name="atl-collection-and-enumerator-classes"></a>Klasy kolekcji ATL i wyliczeń

ATL zawiera następujące klasy w celu ułatwienia implementacji kolekcje i wyliczenia.

|Class|Opis|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementacja interfejsu kolekcji|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implementacja interfejsu modułu wyliczającego (przy założeniu — dane przechowywane w kontenerze zgodnej biblioteki C++ Standard)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implementacja interfejsu modułu wyliczającego (przy założeniu — dane przechowywane w tablicy)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementacja obiekt modułu wyliczającego (używa `IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementacja obiekt modułu wyliczającego (używa `CComEnumImpl`)|
|[_Kopiuj](../atl/atl-copy-policy-classes.md)|Klasy zasad kopii|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Klasy zasad kopii|
|[CAdapt](../atl/reference/cadapt-class.md)|Klasa karty (ukrywa **operator &** umożliwiając `CComPtr`, `CComQIPtr`, i `CComBSTR` mają być przechowywane w kontenerach standardowa biblioteka C++)|

## <a name="see-also"></a>Zobacz też

[Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

