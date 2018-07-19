---
title: Klasa CComAutoDeleteCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b90afb9ae47ced33c331aef988489b567b1078b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879905"
---
# <a name="ccomautodeletecriticalsection-class"></a>Klasa CComAutoDeleteCriticalSection
Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Uwagi  
 `CComAutoDeleteCriticalSection` pochodzi z klasy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Jednak `CComAutoDeleteCriticalSection` zastępuje [termin](ccomsafedeletecriticalsection-class.md#term) metody **prywatnej** dostępu, co zmusza czyszczenia pamięci wewnętrznej, tylko wtedy, gdy wystąpienia tej klasy wykraczają poza zakres lub jawnie są usuwane z ilość pamięci.  

  
 Ta klasa wprowadza żadnych dodatkowych metod za pośrednictwem swojej klasy bazowej. Zobacz [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) i [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) więcej informacji na temat klas pomocniczych sekcję krytyczną.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
