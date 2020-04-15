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
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318994"
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
|[CAtlException::operator HRESULT](#operator_hresult)|Rzutuje bieżący obiekt na wartość HRESULT.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|Zmienna typu HRESULT utworzona przez obiekt i używana do przechowywania warunku błędu.|

## <a name="remarks"></a>Uwagi

Obiekt `CAtlException` reprezentuje warunek wyjątku związane z operacją ATL. Klasa `CAtlException` zawiera element członkowski danych publicznych, który przechowuje kod stanu wskazujący przyczynę wyjątku i operator rzutowania, który pozwala traktować wyjątek tak, jakby był HRESULT.

Ogólnie rzecz biorąc, `AtlThrow` będzie wywoływać, a nie tworzenie `CAtlException` obiektu bezpośrednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Konstruktor.

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Kod błędu HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::operator HRESULT

Rzutuje bieżący obiekt na wartość HRESULT.

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException::m_hr

Element członkowski danych HRESULT.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych, który przechowuje warunek błędu. Wartość HRESULT jest ustawiana przez konstruktora [CAtlException::CAtlException](#catlexception).

## <a name="see-also"></a>Zobacz też

[AtlThrow ( AtlThrow )](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
