---
title: Klasa CD2DPointU | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
dev_langs: C++
helpviewer_keywords: CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d2c7525e5b4626fa2075c5f609ca2fa3affcfc4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU  
 Tworzy obiekt CD2DPointU z CPoint obiektu.  
  
```  
CD2DPointU(const CPoint& pt);  
CD2DPointU(const D2D1_POINT_2U& pt);  
  CD2DPointU(const D2D1_POINT_2U* pt);  
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 źródłowy punkt  
  
 `uX`  
 Źródło X  
  
 `uY`  
 Źródło Y  
  
##  <a name="operator_cpoint"></a>CD2DPointU::operator CPoint  
 Konwertuje obiekt CPoint CD2DPointU.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość D2D punktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
