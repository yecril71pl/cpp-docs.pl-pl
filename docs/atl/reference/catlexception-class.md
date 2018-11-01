---
title: Klasa CAtlException
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: d8ad46fa219ec29c7973677e2184e7b6d65c74b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468877"
---
# <a name="catlexception-class"></a>Klasa CAtlException

Ta klasa definiuje wyjątek ATL.

## <a name="syntax"></a>Składnia

```
class CAtlException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|Rzutuje bieżący obiekt, aby wartość HRESULT.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|Zmienna typu HRESULT utworzony przez obiekt i używane do przechowywania warunku błędu.|

## <a name="remarks"></a>Uwagi

Element `CAtlException` obiektu przedstawia warunek wyjątku związany z operacją ATL. `CAtlException` Klasa zawiera element członkowski danych publicznego, który przechowuje kod stanu wskazujący przyczynę wyjątku oraz operator rzutowania, który umożliwia traktowanie wyjątek, tak jakby HRESULT.

Ogólnie rzecz biorąc, wywoła `AtlThrow` zamiast tworzenia `CAtlException` obiektu bezpośrednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlexcept.h

##  <a name="catlexception"></a>  CAtlException::CAtlException

Konstruktor.

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Kod błędu HRESULT.

##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT

Rzutuje bieżący obiekt, aby wartość HRESULT.

```
operator HRESULT() const throw ();
```

##  <a name="m_hr"></a>  CAtlException::m_hr

Element członkowski danych HRESULT.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych, który przechowuje warunku błędu. Wartość HRESULT jest ustawiana przez konstruktora, [CAtlException::CAtlException](#catlexception).

## <a name="see-also"></a>Zobacz też

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
