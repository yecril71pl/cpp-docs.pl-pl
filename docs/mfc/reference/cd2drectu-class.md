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
ms.openlocfilehash: d5faf4bb8f2ff416d90311d678543c48d212acdd
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953886"
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
|[CD2DRectU::CD2DRectU](#cd2drectu)|Przeciążone. Konstruuje `CD2DRectU` obiekt z `D2D1_RECT_U` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|Zwraca **logiczna** wartość, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych ( **null**).|  
  
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
 *Rect*  
 Prostokąt źródła  
  
 *uLeft*  
 Lewa współrzędna źródła  
  
 *uTop*  
 Górna współrzędna źródła  
  
 *uRight*  
 prawa Współrzędna źródła  
  
 *uBottom*  
 Współrzędna dolnej źródła  
  
##  <a name="isnull"></a>  CD2DRectU::IsNull  
 Zwraca wartość logiczną, wskazującą, czy wyrażenie nie zawiera prawidłowych danych (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli prostokąta top, lewej dolnej i prawej wartości są równe 0; w przeciwnym razie wartość FALSE.  
  
##  <a name="operator_crect"></a>  CD2DRectU::operator CRect  
 Konwertuje obiekt CRect CD2DRectU.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość D2D prostokąta.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
