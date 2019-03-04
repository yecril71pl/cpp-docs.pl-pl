---
title: CComCritSecLock Class
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
ms.openlocfilehash: 045e64504707fa8978c8236b376037d9f57bf12c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261235"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock Class

Ta klasa dostarcza metody do blokowanie i odblokowywanie obiektu sekcję krytyczną.

## <a name="syntax"></a>Składnia

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parametry

*TLock*<br/>
Obiekt, który może zostać zablokowany i odblokować.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor.|
|[CComCritSecLock::~CComCritSecLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Wywołaj tę metodę można zablokować obiektu sekcję krytyczną.|
|[CComCritSecLock::Unlock](#unlock)|Wywołaj tę metodę w celu odblokowania obiektu sekcję krytyczną.|

## <a name="remarks"></a>Uwagi

Ta klasa umożliwia blokowanie i odblokowywanie obiektów w bezpieczniejszy sposób niż przy użyciu [klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) lub [klasa CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

Konstruktor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Obiekt sekcję krytyczną.

*bInitialLock*<br/>
Stan początkowy blokady: **true** oznacza, że zablokowane.

### <a name="remarks"></a>Uwagi

Inicjuje obiekt sekcję krytyczną.

##  <a name="dtor"></a>  CComCritSecLock::~CComCritSecLock

Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Uwagi

Odblokowuje obiektu sekcję krytyczną.

##  <a name="lock"></a>  CComCritSecLock::Lock

Wywołaj tę metodę można zablokować obiektu sekcję krytyczną.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK, jeśli obiekt został pomyślnie zablokowany lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest już zablokowany, wystąpi błąd ASERCJI w kompilacjach do debugowania.

##  <a name="unlock"></a>  CComCritSecLock::Unlock

Wywołaj tę metodę w celu odblokowania obiektu sekcję krytyczną.

```
void Unlock() throw();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest już odblokowane, wystąpi błąd ASERCJI w kompilacjach do debugowania.

## <a name="see-also"></a>Zobacz także

[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klasa CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)
