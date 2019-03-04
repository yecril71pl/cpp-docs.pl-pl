---
title: Klasa CComApartment
ms.date: 11/04/2016
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
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 92db42a45a0863f8b43f7c46da9624e424d1e488
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290108"
---
# <a name="ccomapartment-class"></a>Klasa CComApartment

Ta klasa obsługuje zarządzanie mieszkania w module EXE wątków w puli.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CComApartment::GetLockCount](#getlockcount)|Zwraca liczbę blokad z bieżącego wątku.|
|[CComApartment::Lock](#lock)|Zwiększa liczbę blokad wątku.|
|[CComApartment::Unlock](#unlock)|Zmniejsza liczbę blokad wątku.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Zawiera identyfikator wątku.|
|[CComApartment::m_hThread](#m_hthread)|Zawiera dojście wątku.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Zawiera liczbę blokad z bieżącego wątku.|

## <a name="remarks"></a>Uwagi

`CComApartment` jest używany przez [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) do zarządzania typu apartment w module EXE wątków w puli. `CComApartment` udostępnia metody zwiększanie i zmniejszanie blokady możesz liczyć na wątek.

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

Automatycznie ustawiona podczas [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

Konstruktor.

```
CComApartment();
```

### <a name="remarks"></a>Uwagi

Inicjuje `CComApartment` elementy członkowskie danych [m_nLockCnt](#m_nlockcnt) i [m_hThread](#m_hthread).

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

Zwraca liczbę blokad z bieżącego wątku.

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

Wartość, która może być użyteczna, diagnostykę lub testowania.

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

Zawiera liczbę blokad z bieżącego wątku.

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

Zmniejsza liczbę blokad wątku.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

### <a name="remarks"></a>Uwagi

Wywoływane przez [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Liczba blokad w wątku jest używana do celów statystycznych.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
