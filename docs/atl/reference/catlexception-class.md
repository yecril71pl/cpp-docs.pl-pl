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
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168205"
---
# <a name="catlexception-class"></a>Klasa CAtlException

Ta klasa definiuje wyjątek ATL.

## <a name="syntax"></a>Składnia

```cpp
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
|[CAtlException:: operator HRESULT](#operator_hresult)|Rzutuje bieżący obiekt na wartość HRESULT.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlException:: m_hr](#m_hr)|Zmienna typu HRESULT utworzona przez obiekt i używana do przechowywania warunku błędu.|

## <a name="remarks"></a>Uwagi

`CAtlException` Obiekt reprezentuje warunek wyjątku związany z operacją ATL. `CAtlException` Klasa zawiera publiczny element członkowski danych, który przechowuje kod stanu wskazujący przyczynę wyjątku i operatora rzutowania, który umożliwia traktowanie wyjątku, tak jakby był to wynik HRESULT.

Ogólnie rzecz biorąc `AtlThrow` zamiast bezpośrednio utworzyć `CAtlException` obiekt.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlexcept. h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Konstruktor.

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parametry

*wysoki*<br/>
Kod błędu HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException:: operator HRESULT

Rzutuje bieżący obiekt na wartość HRESULT.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException:: m_hr

Element członkowski danych HRESULT.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych, który przechowuje warunek błędu. Wartość HRESULT jest ustawiana przez konstruktora, [CAtlException:: CAtlException](#catlexception).

## <a name="see-also"></a>Zobacz także

[Funkcji AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
