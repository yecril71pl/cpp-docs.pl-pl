---
title: Klasa CComFakeCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a042e52439579cfb1b4145b1691f5a00128754c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358618"
---
# <a name="ccomfakecriticalsection-class"></a>Klasa CComFakeCriticalSection
Ta klasa zawiera te same metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale nie zawiera sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.|  
|[CComFakeCriticalSection::Lock](#lock)|Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.|  
|[CComFakeCriticalSection::Term](#term)|Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.|  
|[CComFakeCriticalSection::Unlock](#unlock)|Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.|  
  
## <a name="remarks"></a>Uwagi  
 `CComFakeCriticalSection` odzwierciedla metod w [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComFakeCriticalSection` nie zawiera sekcja krytyczna; w związku z tym jego metody nic nie rób.  
  
 Zazwyczaj `CComFakeCriticalSection` za pośrednictwem `typedef` name, albo `AutoCriticalSection` lub `CriticalSection`. Korzystając z [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), oba te `typedef` nazwy odwołania `CComFakeCriticalSection`. Korzystając z [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), odwołujących się do [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) i `CComCriticalSection`odpowiednio.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="init"></a>  CComFakeCriticalSection::Init  
 Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="lock"></a>  CComFakeCriticalSection::Lock  
 Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="term"></a>  CComFakeCriticalSection::Term  
 Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock  
 Nie działają, ponieważ nie istnieje żadna sekcja krytyczna.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
