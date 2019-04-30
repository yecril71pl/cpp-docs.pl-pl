---
title: CD2DRectU Class
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
ms.openlocfilehash: feb8af3992b9f56164ded0e3b6a4529a46fe2a1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396291"
---
# <a name="cd2drectu-class"></a>CD2DRectU Class

Otoka dla `D2D1_RECT_U`.

## <a name="syntax"></a>Składnia

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Przeciążone. Konstruuje `CD2DRectU` obiektu z `D2D1_RECT_U` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Zwraca **logiczna** wartość, która wskazuje, czy wyrażenie nie zawiera żadnych prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|Konwertuje `CD2DRectU` do `CRect` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

Tworzy obiekt CD2DRectU z CRect obiektu.

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
prostokąta źródłowego

*uLeft*<br/>
Współrzędna lewej źródła

*uTop*<br/>
współrzędne źródła

*uRight*<br/>
Źródło bezpośrednio współrzędnych

*uBottom*<br/>
Współrzędna dolnej źródła

##  <a name="isnull"></a>  CD2DRectU::IsNull

Zwraca wartość logiczną wskazującą, czy wyrażenie nie zawiera żadnych prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli góry prostokąta, po lewej stronie, dolnej i odpowiednie wartości są równe 0; w przeciwnym razie wartość FALSE.

##  <a name="operator_crect"></a>  CD2DRectU::operator CRect

Konwertuje CD2DRectU CRect obiektu.

```
operator CRect();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
