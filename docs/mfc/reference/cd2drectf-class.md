---
title: Klasa CD2DRectF
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369121"
---
# <a name="cd2drectf-class"></a>Klasa CD2DRectF

Otoka dla `D2D1_RECT_F`.

## <a name="syntax"></a>Składnia

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectf::CD2DRectF](#cd2drectf)|Przeciążone. Konstruuje `CD2DRectF` obiekt `D2D1_RECT_F` z obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectf::Isnull](#isnull)|Zwraca wartość **logiczną,** która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF::operator CRect](#operator_crect)|`CD2DRectF` Konwertuje `CRect` na obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DRectf::CD2DRectF

Konstruuje obiekt CD2DRectF z obiektu CRect.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
prostokąt źródłowy

*fNaft*<br/>
źródło lewa współrzędna

*fTop*<br/>
współrzędna górna źródła

*Strach*<br/>
współrzędna prawej strony źródła

*fBottom (właśc.*<br/>
współrzędna dolna źródło

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DRectf::Isnull

Zwraca wartość logiczną, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wartości górne, lewe, dolne i prawe prostokąta są równe wartości 0; w przeciwnym razie FALSE.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::operator CRect

Konwertuje obiekt CD2DRectF na obiekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
