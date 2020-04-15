---
title: Klasa CComCriticalSekcja
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327966"
---
# <a name="ccomcriticalsection-class"></a>Klasa CComCriticalSekcja

Ta klasa zawiera metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSekcja::CComCriticalSection](#ccomcriticalsection)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSekcja::Init](#init)|Tworzy i inicjuje obiekt sekcji krytycznej.|
|[CComCriticalSekcja::Lock](#lock)|Uzyskuje własność obiektu sekcji krytycznej.|
|[CComCriticalSekcja::Termin](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcji krytycznej.|
|[CComCriticalSection::Odblokuj](#unlock)|Zwalnia własność obiektu sekcji krytycznej.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSekcja::m_sec](#m_sec)|Obiekt CRITICAL_SECTION.|

## <a name="remarks"></a>Uwagi

`CComCriticalSection`jest podobny do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), z tą różnicą, że należy jawnie zainicjować i zwolnić sekcję krytyczną.

Zazwyczaj używa `CComCriticalSection` się za pomocą **nazwy typedef** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ta nazwa `CComCriticalSection` odwołuje się, gdy [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używany.

Zobacz [CComCritSecLock Klasy](../../atl/reference/ccomcritseclock-class.md) bezpieczniejszy sposób korzystania `Lock` z `Unlock` tej klasy niż wywołanie i bezpośrednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CComCriticalSekcja::CComCriticalSection

Konstruktor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Ustawia [element](#m_sec) członkowski m_sec danych na NULL.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSekcja::Init

Wywołuje funkcję Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), która inicjuje obiekt sekcji krytycznej zawarty w [m_sec](#m_sec) element członkowski danych.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces, E_OUTOFMEMORY lub E_FAIL na niepowodzenie.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CComCriticalSekcja::Lock

Wywołuje funkcję Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), która czeka, aż wątek może przejąć na własność obiekt sekcji krytycznej zawarte w [m_sec](#m_sec) element członkowski danych.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces, E_OUTOFMEMORY lub E_FAIL na niepowodzenie.

### <a name="remarks"></a>Uwagi

Obiekt sekcji krytycznej musi najpierw zostać zainicjowany wywołaniem metody [Init.](#init) Po zakończeniu wykonywania chronionego kodu wątek musi [wywołać Unlock,](#unlock) aby zwolnić własność sekcji krytycznej.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSekcja::m_sec

Zawiera obiekt sekcji krytycznej, `CComCriticalSection` który jest używany przez wszystkie metody.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CComCriticalSekcja::Termin

Wywołuje funkcję Win32 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), która zwalnia wszystkie zasoby używane przez obiekt sekcji krytycznej zawarte w [m_sec](#m_sec) element członkowski danych.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Po `Term` wywołaniu sekcji krytycznej nie można już używać do synchronizacji.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CComCriticalSection::Odblokuj

Wywołuje funkcję Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), która zwalnia własność obiektu sekcji krytycznej zawartej w [m_sec](#m_sec) element członkowski danych.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby najpierw uzyskać własność, wątek musi wywołać [Lock](#lock) metody. Każde wywołanie `Lock` wymaga odpowiedniego `Unlock` wywołania, aby zwolnić własność sekcji krytycznej.

## <a name="see-also"></a>Zobacz też

[CComFakeCriticalKuction Klasa](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
