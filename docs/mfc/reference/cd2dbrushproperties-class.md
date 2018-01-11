---
title: Klasa CD2DBrushProperties | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
dev_langs: C++
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 011ea92e24be73aa51e29bab327bfa1ccdf7ed9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Przeciążone. Tworzy `CD2D_BRUSH_PROPERTIES` — struktura|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicjuje obiekt|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_BRUSH_PROPERTIES`  
  
 `CD2DBrushProperties`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2dbrushproperties"></a>CD2DBrushProperties::CD2DBrushProperties  
 Tworzy strukturę CD2D_BRUSH_PROPERTIES  
  
```  
CD2DBrushProperties();  
CD2DBrushProperties(FLOAT _opacity);

 
CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,  
    FLOAT _opacity = 1.);
```  
  
### <a name="parameters"></a>Parametry  
 `_opacity`  
 Podstawowy przezroczystość pędzla. Wartość domyślna to 1.0.  
  
 `_transform`  
 Przekształcenie do zastosowania pędzla  
  
##  <a name="commoninit"></a>CD2DBrushProperties::CommonInit  
 Inicjuje obiekt  
  
```  
void CommonInit();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
