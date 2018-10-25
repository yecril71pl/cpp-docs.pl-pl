---
title: Klasa CD2DRectU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3fc66e5cc116ce97a9abead8eeb6607f7a36ef7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052684"
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

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
