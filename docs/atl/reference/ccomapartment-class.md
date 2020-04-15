---
title: Klasa CComapartment
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
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321115"
---
# <a name="ccomapartment-class"></a>Klasa CComapartment

Ta klasa zapewnia obsługę zarządzania mieszkaniem w module EXE z puli wątków.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CComapartment::Apartament](#apartment)|Oznacza adres początkowy wątku.|
|[CComApartment::GetLockCount](#getlockcount)|Zwraca bieżącą liczbę blokad wątku.|
|[CComApartment::Lock](#lock)|Zwiększa liczbę blokad wątku.|
|[CComApartment::Odblokuj](#unlock)|Zmniejsza liczbę blokad wątku.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Zawiera identyfikator wątku.|
|[CComApartment::m_hThread](#m_hthread)|Zawiera uchwyt wątku.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Zawiera bieżącą liczbę blokad wątku.|

## <a name="remarks"></a>Uwagi

`CComApartment`jest używany przez [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) do zarządzania mieszkaniem w module EXE z puli wątków. `CComApartment`udostępnia metody zwiększania i zmniejszania liczby blokad w wątku.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CComapartment::Apartament

Oznacza adres początkowy wątku.

```
DWORD Apartment();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze 0.

### <a name="remarks"></a>Uwagi

Automatycznie ustawiany podczas [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CComApartment::CComApartment

Konstruktor.

```
CComApartment();
```

### <a name="remarks"></a>Uwagi

Inicjuje `CComApartment` elementy członkowskie danych [m_nLockCnt](#m_nlockcnt) i [m_hThread](#m_hthread).

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CComApartment::GetLockCount

Zwraca bieżącą liczbę blokad wątku.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba blokad na wątku.

## <a name="ccomapartmentlock"></a><a name="lock"></a>CComApartment::Lock

Zwiększa liczbę blokad wątku.

```
LONG Lock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wywoływany przez [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Liczba blokad na wątku jest używana do celów statystycznych.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CComApartment::m_dwThreadID

Zawiera identyfikator wątku.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CComApartment::m_hThread

Zawiera uchwyt wątku.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CComApartment::m_nLockCnt

Zawiera bieżącą liczbę blokad wątku.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CComApartment::Odblokuj

Zmniejsza liczbę blokad wątku.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wywoływany przez [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Liczba blokad na wątku jest używana do celów statystycznych.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
