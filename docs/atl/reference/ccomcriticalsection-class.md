---
title: Klasa CComCriticalSection
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
ms.openlocfilehash: ee4ce32ed4ae04bc3b390af5cf104b8a0af599f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497280"
---
# <a name="ccomcriticalsection-class"></a>Klasa CComCriticalSection

Ta klasa zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSection:: init](#init)|Tworzy i inicjuje obiekt sekcji krytycznej.|
|[CComCriticalSection::Lock](#lock)|Uzyskuje własność obiektu sekcji krytycznej.|
|[CComCriticalSection:: Term](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcji krytycznej.|
|[CComCriticalSection:: Unlock](#unlock)|Zwalnia własność obiektu sekcji krytycznej.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Obiekt CRITICAL_SECTION.|

## <a name="remarks"></a>Uwagi

`CComCriticalSection`jest podobna do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), z tą różnicą, że należy jawnie zainicjować i zwolnić sekcję krytyczną.

Zwykle używany `CComCriticalSection` przez **element typedef** Name [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ta nazwa odwołuje `CComCriticalSection` się, gdy jest używana [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Zobacz [CComCritSecLock klasy](../../atl/reference/ccomcritseclock-class.md) , aby bezpiecznie używać tej klasy niż wywoływanie `Lock` i `Unlock` bezpośrednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

Konstruktor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski danych [m_sec](#m_sec) na wartość null.

##  <a name="init"></a>CComCriticalSection:: init

Wywołuje funkcję Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), która inicjuje obiekt sekcji krytycznej zawarty w elemencie członkowskim danych [m_sec](#m_sec) .

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK w przypadku powodzenia, E_OUTOFMEMORY lub E_FAIL w przypadku niepowodzenia.

##  <a name="lock"></a>CComCriticalSection:: Lock

Wywołuje funkcję Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), która czeka, aż wątek może przejąć własność obiektu sekcji krytycznej zawartego w składowej danych [m_sec](#m_sec) .

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK w przypadku powodzenia, E_OUTOFMEMORY lub E_FAIL w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Należy najpierw zainicjować obiekt sekcji krytycznej przy użyciu wywołania metody [init](#init) . Gdy chroniony kod zakończył wykonywanie, wątek musi wywołać metodę [Unlock](#unlock) , aby zwolnić własność sekcji krytycznej.

##  <a name="m_sec"></a>CComCriticalSection::m_sec

Zawiera obiekt sekcji krytycznej, który jest używany przez `CComCriticalSection` wszystkie metody.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>CComCriticalSection:: Term

Wywołuje funkcję Win32 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), która zwalnia wszystkie zasoby używane przez obiekt sekcji krytycznej zawarty w elemencie członkowskim danych [m_sec](#m_sec) .

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Po `Term` wywołaniu nie można już użyć sekcji krytycznej do synchronizacji.

##  <a name="unlock"></a>CComCriticalSection:: Unlock

Wywołuje funkcję Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), która zwalnia własność obiektu sekcji krytycznej zawartego w składowej danych [m_sec](#m_sec) .

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby najpierw uzyskać własność, wątek musi wywołać metodę [Lock](#lock) . Każde wywołanie `Lock` wymaga odpowiedniego `Unlock` wywołania, aby zwolnić własność sekcji krytycznej.

## <a name="see-also"></a>Zobacz także

[Klasa CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
