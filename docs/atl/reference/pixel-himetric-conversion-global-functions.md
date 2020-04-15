---
title: Globalne funkcje konwersji PIXEL-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326141"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globalne funkcje konwersji pikseli/HIMETRIC

Funkcje te zapewniają obsługę konwersji do i z jednostek pikseli i HIMETRIC.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlHiMetricToPixel (AtlHiMetricToPixel)](#atlhimetrictopixel)|Konwertuje jednostki HIMETRIC (każda jednostka ma 0,01 milimetra) na piksele.|
|[AtlPixelToHiMetric (AtlPixelToHiMetric)](#atlpixeltohimetric)|Konwertuje piksele na jednostki HIMETRIC (każda jednostka ma 0,01 milimetra).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>AtlHiMetricToPixel (AtlHiMetricToPixel)

Konwertuje rozmiar obiektu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra) na rozmiar w pikselach na ekranie urządzenia.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
[w] Wskaźnik do rozmiaru obiektu w jednostkach HIMETRIC.

*lpSizeInPix*<br/>
[na zewnątrz] Wskaźnik do miejsca, w którym ma zostać zwrócony rozmiar obiektu w pikselach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixelToHiMetric (AtlPixelToHiMetric)

Konwertuje rozmiar obiektu w pikselach na ekranie urządzenia na rozmiar w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
[w] Wskaźnik do rozmiaru obiektu w pikselach.

*lpSizeInHiMetric*<br/>
[na zewnątrz] Wskaźnik do miejsca, w którym ma zostać zwrócony rozmiar obiektu w jednostkach HIMETRIC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
