---
title: Klasa CD2DPointU
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 8c6db55f1dde1fd054a1f75590f5969c097b2f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369143"
---
# <a name="cd2dpointu-class"></a>Klasa CD2DPointU

Otoka dla `D2D1_POINT_2U`.

## <a name="syntax"></a>Składnia

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Przeciążone. Konstruuje `CD2DPointU` obiekt `D2D1_POINT_2U` z obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|`CD2DPointU` Konwertuje `CPoint` na obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dpointucd2dpointu"></a><a name="cd2dpointu"></a>CD2DPointU::CD2DPointU

Konstruuje obiekt CD2DPointU z obiektu CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
punkt źródłowy

*Ux*<br/>
źródło X

*Uy*<br/>
źródło Y

## <a name="cd2dpointuoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointU::operator CPoint

Konwertuje obiekt CD2DPointU na CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość punktu D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
