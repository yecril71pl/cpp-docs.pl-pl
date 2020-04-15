---
title: Klasa CComCritSecLock
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 24d141c5b0ec703feadcd7db96da33f9de940dda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327948"
---
# <a name="ccomcritseclock-class"></a>Klasa CComCritSecLock

Ta klasa zawiera metody blokowania i odblokowywania obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parametry

*TLock (śluza)*<br/>
Obiekt, który ma być zablokowany i odblokowany.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor.|
|[CComCritSecLock::~CComCritSecLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Wywołanie tej metody, aby zablokować obiekt sekcji krytycznej.|
|[CComCritSecLock::Odblokuj](#unlock)|Wywołanie tej metody, aby odblokować obiekt sekcji krytycznej.|

## <a name="remarks"></a>Uwagi

Ta klasa służy do blokowania i odblokowywania obiektów w bezpieczniejszy sposób niż w [przypadku klasy CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) lub [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

Konstruktor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Obiekt sekcji krytycznej.

*bInitialLock*<br/>
Początkowy stan blokady: **true** oznacza zablokowany.

### <a name="remarks"></a>Uwagi

Inicjuje obiekt sekcji krytycznej.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock::~CComCritSecLock

Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Uwagi

Odblokowuje obiekt sekcji krytycznej.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock::Lock

Wywołanie tej metody, aby zablokować obiekt sekcji krytycznej.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli obiekt został pomyślnie zablokowany lub błąd HRESULT w przypadku awarii.

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest już zablokowany, błąd ASSERT wystąpi w kompilacjach debugowania.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock::Odblokuj

Wywołanie tej metody, aby odblokować obiekt sekcji krytycznej.

```
void Unlock() throw();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest już odblokowany, błąd ASSERT wystąpi w kompilacjach debugowania.

## <a name="see-also"></a>Zobacz też

[Klasa CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klasa CComAutoCriticalSekcja](../../atl/reference/ccomautocriticalsection-class.md)
