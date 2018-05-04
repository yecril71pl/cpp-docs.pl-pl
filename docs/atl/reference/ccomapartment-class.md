---
title: Klasa CComApartment | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88e08d50cec36366df2423d31082b97d41b5061f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomapartment-class"></a>Klasa CComApartment
Ta klasa obsługuje zarządzanie mieszkania w module EXE puli wątków.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComApartment
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|Oznacza adres początkowy wątku.|  
|[CComApartment::GetLockCount](#getlockcount)|Zwraca liczbę blokad bieżącego wątku.|  
|[CComApartment::Lock](#lock)|Zwiększa liczbę blokad wątku.|  
|[CComApartment::Unlock](#unlock)|Zmniejsza liczbę blokad wątku.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Zawiera identyfikator wątku.|  
|[CComApartment::m_hThread](#m_hthread)|Zawiera dojście wątku.|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Zawiera liczbę blokad bieżącego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `CComApartment` jest używany przez [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) Zarządzanie typu apartment w module EXE puli wątków. `CComApartment` udostępnia metody zwiększanie oraz zmniejszanie blokady liczba w wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="apartment"></a>  CComApartment::Apartment  
 Oznacza adres początkowy wątku.  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze 0.  
  
### <a name="remarks"></a>Uwagi  
 Automatycznie ustawione podczas [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).  
  
##  <a name="ccomapartment"></a>  CComApartment::CComApartment  
 Konstruktor.  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CComApartment` elementy członkowskie danych [m_nLockCnt](#m_nlockcnt) i [m_hThread](#m_hthread).  
  
##  <a name="getlockcount"></a>  CComApartment::GetLockCount  
 Zwraca liczbę blokad bieżącego wątku.  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba blokad w wątku.  
  
##  <a name="lock"></a>  CComApartment::Lock  
 Zwiększa liczbę blokad wątku.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Liczba blokad w wątku jest używana do celów statystycznych.  
  
##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID  
 Zawiera identyfikator wątku.  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>  CComApartment::m_hThread  
 Zawiera dojście wątku.  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt  
 Zawiera liczbę blokad bieżącego wątku.  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>  CComApartment::Unlock  
 Zmniejsza liczbę blokad wątku.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Liczba blokad w wątku jest używana do celów statystycznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
