---
title: Funkcje globalne konwersji HIMETRIC pikseli
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 95b3b9c6ba4e5d25a9f07f72f9479121a223ad00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529106"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funkcje globalne konwersji HIMETRIC/pikseli

Te funkcje zapewniają obsługę konwersji do i z pikseli i jednostkach HIMETRIC.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Konwertuje jednostkach HIMETRIC (każda jednostka to 0,01 milimetra) pikseli.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Konwertuje pikseli w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra).|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

Konwertuje rozmiar obiektu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra) na rozmiar w pikselach na ekranie urządzenia.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
[in] Wskaźnik na rozmiar obiektu w jednostkach HIMETRIC.

*lpSizeInPix*<br/>
[out] Wskaźnik do której jest zwracana rozmiar obiektu w pikselach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

Konwertuje rozmiar obiektu w pikselach na ekranie urządzenia na rozmiar w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
[in] Wskaźnik na rozmiar obiektu w pikselach.

*lpSizeInHiMetric*<br/>
[out] Wskaźnik do której rozmiar obiektu w jednostkach HIMETRIC ma zostać zwrócone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
