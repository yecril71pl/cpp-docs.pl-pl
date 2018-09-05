---
title: Klasa CDefaultCharTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 080a7b9f5da71535f8b141555ec1890a521fe715
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761985"
---
# <a name="cdefaultchartraits-class"></a>Klasa CDefaultCharTraits

Ta klasa udostępnia dwie funkcje statyczne konwersję znaków między wielkimi i małymi.

## <a name="syntax"></a>Składnia

```
template <typename T>  
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parametry

*T*  
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statyczny) Wywołaj tę funkcję w celu konwersji znaków na wielkie litery.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statyczny) Wywołaj tę funkcję w celu konwersji znaków na małe litery.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia funkcje, które są wykorzystywane przez klasę [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

Wywołaj tę funkcję w celu konwersji znaków na małe litery.

```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```

### <a name="parameters"></a>Parametry

*x*  
Znak do przekonwertowania na małe litery.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

Wywołaj tę funkcję w celu konwersji znaków na wielkie litery.

```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parametry

*x*  
Znak do przekonwertowania na wielkie litery.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
