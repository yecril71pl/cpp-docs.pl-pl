---
title: Kolekcja ATL i klasy modułu wyliczającego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a47525bb21b896b0fef8393cab66142ed40311ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-collection-and-enumerator-classes"></a>Moduł wyliczający klasy i kolekcji ATL
ATL zawiera następujące klasy w celu ułatwienia implementacji kolekcje i wyliczenia.  
  
|Class|Opis|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementacja interfejsu kolekcji|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implementacja interfejsu modułu wyliczającego (przy założeniu danych przechowywanych w kontenerze zgodnej biblioteki C++ Standard)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implementacja interfejsu modułu wyliczającego (przy założeniu dane przechowywane w tablicy)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementacja obiektu modułu wyliczającego (używa `IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementacja obiektu modułu wyliczającego (używa `CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|Kopiowanie zasady — klasa|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Kopiowanie zasady — klasa|  
|[CAdapt](../atl/reference/cadapt-class.md)|Klasa karty (ukrywa **operatora &** stosowanie `CComPtr`, `CComQIPtr`, i `CComBSTR` mają być przechowywane w kontenerach standardowa biblioteka C++)|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

