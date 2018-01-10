---
title: Klasa CD2DPointF | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs: C++
helpviewer_keywords: CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b369be53d14af49eb112026089226214f0d7d73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpointf-class"></a>Klasa CD2DPointF
Otoka dla `D2D1_POINT_2F`.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Przeciążone. Konstruuje `CD2DPointF` obiekt z `D2D1_POINT_2F` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DPointF::operator CPoint](#operator_cpoint)|Konwertuje `CD2DPointF` do `CPoint` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>CD2DPointF::CD2DPointF  
 Tworzy obiekt CD2DPointF z CPoint obiektu.  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 źródłowy punkt  
  
 `fX`  
 Źródło X  
  
 `fY`  
 Źródło Y  
  
##  <a name="operator_cpoint"></a>CD2DPointF::operator CPoint  
 Konwertuje obiekt CPoint CD2DPointF.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość D2D punktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
