---
title: Klasa CD2DBrushProperties
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: bf6399d2a245addb7e2e65100d33643fcd54e893
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369286"
---
# <a name="cd2dbrushproperties-class"></a>Klasa CD2DBrushProperties

Otoka dla `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Składnia

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WŁAŚCIWOŚCI CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Przeciążone. Tworzy `CD2D_BRUSH_PROPERTIES` strukturę|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[WŁAŚCIWOŚCI CD2DBrushProperties::CommonInit](#commoninit)|Inicjuje obiekt|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>WŁAŚCIWOŚCI CD2DBrushProperties::CD2DBrushProperties

Tworzy strukturę CD2D_BRUSH_PROPERTIES

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Parametry

*_opacity*<br/>
Podstawowe krycie pędzla. Wartość domyślna to 1.0.

*_transform*<br/>
Transformacja stosowana do pędzla

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>WŁAŚCIWOŚCI CD2DBrushProperties::CommonInit

Inicjuje obiekt

```
void CommonInit();
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
