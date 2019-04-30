---
title: CD2DPointU Class
ms.date: 11/04/2016
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: d66793abbb83015891df348eef8384e5c97baf2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396317"
---
# <a name="cd2dpointu-class"></a>CD2DPointU Class

Otoka dla `D2D1_POINT_2U`.

## <a name="syntax"></a>Składnia

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Przeciążone. Konstruuje `CD2DPointU` z obiektu `D2D1_POINT_2U` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|Konwertuje `CD2DPointU` do `CPoint` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Tworzy obiekt CD2DPointU z CPoint obiektu.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
  CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
źródłowy punkt

*środowiska użytkownika*<br/>
Źródło X

*uY*<br/>
Źródło Y

##  <a name="operator_cpoint"></a>  CD2DPointU::operator CPoint

Konwertuje CD2DPointU CPoint obiektu.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość punktu D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
