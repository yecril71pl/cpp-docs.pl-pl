---
title: Klasy kolekcji ATL i wyliczeń
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265408"
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
|[_Copy](../atl/atl-copy-policy-classes.md)|Klasy zasad kopii|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Klasy zasad kopii|
|[CAdapt](../atl/reference/cadapt-class.md)|Klasa karty (ukrywa **operator &** umożliwiając `CComPtr`, `CComQIPtr`, i `CComBSTR` mają być przechowywane w kontenerach standardowa biblioteka C++)|

## <a name="see-also"></a>Zobacz także

[Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)
