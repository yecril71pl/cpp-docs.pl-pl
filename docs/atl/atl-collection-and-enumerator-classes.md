---
title: Klasy kolekcji ATL i wyliczeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ff5fec4749e08826bab5572149c6cd24a204f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765076"
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

