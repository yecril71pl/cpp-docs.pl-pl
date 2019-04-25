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
ms.openlocfilehash: 5ca791af658ee719b2e6d6ea78f82e23a66edc98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253735"
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
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Przeciążone. Tworzy `CD2D_BRUSH_PROPERTIES` struktury|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicjuje obiekt|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties

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
Podstawowy przezroczystość pędzla. Wartość domyślna to 1.0.

*_transform*<br/>
Przekształcenie do zastosowania pędzla

##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit

Inicjuje obiekt

```
void CommonInit();
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
