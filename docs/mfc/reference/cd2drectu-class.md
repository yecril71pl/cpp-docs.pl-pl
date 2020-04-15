---
title: Klasa CD2DRectU
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369111"
---
# <a name="cd2drectu-class"></a>Klasa CD2DRectU

Otoka dla `D2D1_RECT_U`.

## <a name="syntax"></a>Składnia

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2Drectu::CD2DRectu](#cd2drectu)|Przeciążone. Konstruuje `CD2DRectU` obiekt `D2D1_RECT_U` z obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2Drectu::Isnull](#isnull)|Zwraca wartość **logiczną,** która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|`CD2DRectU` Konwertuje `CRect` na obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2Drectu::CD2DRectu

Konstruuje obiekt CD2DRectU z obiektu CRect.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
prostokąt źródłowy

*uNaft*<br/>
źródło lewa współrzędna

*uTop*<br/>
współrzędna górna źródła

*u W prawo*<br/>
współrzędna prawej strony źródła

*uBottom (właśc.*<br/>
współrzędna dolna źródło

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2Drectu::Isnull

Zwraca wartość logiczną, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wartości górne, lewe, dolne i prawe prostokąta są równe wartości 0; w przeciwnym razie FALSE.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::operator CRect

Konwertuje obiekt CD2DRectU na obiekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
