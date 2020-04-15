---
title: Klasa CDefaultCharTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327090"
---
# <a name="cdefaultchartraits-class"></a>Klasa CDefaultCharTraits

Ta klasa udostępnia dwie funkcje statyczne do konwertowania znaków między wielką i małe litery.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statyczne) Wywołanie tej funkcji, aby przekonwertować znak na wielkie litery.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statyczne) Wywołanie tej funkcji, aby przekonwertować znak na małe litery.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera funkcje, które są wykorzystywane przez klasę [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>CDefaultCharTraits::CharToLower

Wywołanie tej funkcji, aby przekonwertować znak na małe litery.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Znak do konwersji na małe litery.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>CDefaultCharTraits::CharToUpper

Wywołanie tej funkcji, aby przekonwertować znak na wielkie litery.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Znak do przekonwertowania na wielkie litery.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
