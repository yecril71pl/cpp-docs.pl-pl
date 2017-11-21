---
title: Klasa CD2DRectF | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs: C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14938e6e3ccb6cff6247534e0ae321254bf1b9a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[CD2DRectF::CD2DRectF](#cd2drectf)|Przeciążone. Konstruuje `CD2DRectF` obiekt z `D2D1_RECT_F` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|Zwraca `boolean` wartość, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych ( `null`).|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](#operator_crect)|Konwertuje `CD2DRectF` do `CRect` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF  
 Tworzy obiekt CD2DRectF z CRect obiektu.  
  
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
 `rect`  
 Prostokąt źródła  
  
 `fLeft`  
 Lewa współrzędna źródła  
  
 `fTop`  
 Górna współrzędna źródła  
  
 `fRight`  
 prawa Współrzędna źródła  
  
 `fBottom`  
 Współrzędna dolnej źródła  
  
##  <a name="isnull"></a>CD2DRectF::IsNull  
 Zwraca wartość logiczną, wskazującą, czy wyrażenie nie zawiera prawidłowych danych (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli prostokąta top, lewej dolnej i prawej wartości są równe 0; w przeciwnym razie wartość FALSE.  
  
##  <a name="operator_crect"></a>CD2DRectF::operator CRect  
 Konwertuje obiekt CRect CD2DRectF.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość D2D prostokąta.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
