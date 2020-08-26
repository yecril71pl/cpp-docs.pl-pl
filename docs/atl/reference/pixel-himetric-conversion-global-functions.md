---
title: Funkcja globalna konwersji HIMETRIC pikseli
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: e71dccbccbe43ea7df3b6a7005da138a8e31aeb3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834690"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funkcje globalne konwersji pikseli/HIMETRIC

Te funkcje zapewniają obsługę konwersji do i z pikseli i HIMETRIC jednostek.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Konwertuje jednostki HIMETRIC (każda jednostka to 0,01 milimetr) na piksele.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Konwertuje piksele na jednostki HIMETRIC (każda jednostka to 0,01 milimetra).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a> AtlHiMetricToPixel

Konwertuje rozmiar obiektu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra) na rozmiar w pikselach na ekranie urządzenia.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
podczas Wskaźnik na rozmiar obiektu w jednostkach HIMETRIC.

*lpSizeInPix*<br/>
określoną Wskaźnik do miejsca, w którym ma zostać zwrócony rozmiar obiektu w pikselach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a> AtlPixelToHiMetric

Konwertuje rozmiar obiektu w pikselach na ekranie urządzenia na rozmiar w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
podczas Wskaźnik na rozmiar obiektu w pikselach.

*lpSizeInHiMetric*<br/>
określoną Wskaźnik do lokalizacji, w której ma zostać zwrócony rozmiar obiektu w jednostkach HIMETRIC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
