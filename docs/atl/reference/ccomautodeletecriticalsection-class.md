---
title: Klasa CComAutoDeleteCriticalSection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d073e392030db72d6371a798875daf3d7a90e247
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomautodeletecriticalsection-class"></a>Klasa CComAutoDeleteCriticalSection
Ta klasa dostarcza metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Uwagi  
 `CComAutoDeleteCriticalSection`pochodzi z klasy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Jednak `CComAutoDeleteCriticalSection` zastępuje [termin](ccomsafedeletecriticalsection-class.md#term) metodę `private` dostępu, co wymusza czyszczenia pamięci wewnętrznej występuje tylko wtedy, gdy wystąpienia tej klasy się znaleźć poza zakresem lub jawnie są usuwane z pamięci.  

  
 Ta klasa wprowadza żadnych dodatkowych metod w klasie podstawowej. Zobacz [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) i [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) uzyskać więcej informacji na temat klas pomocniczych sekcja krytyczna.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
