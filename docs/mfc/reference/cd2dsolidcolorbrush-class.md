---
title: Klasa CD2DSolidColorBrush | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9020eb0165a0f06e430caa6a0e1641ea1afb3d75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358345"
---
# <a name="cd2dsolidcolorbrush-class"></a>Klasa CD2DSolidColorBrush
Otoka dla ID2D1SolidColorBrush.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Przeciążone. Tworzy obiekt CD2DSolidColorBrush.|  
|[CD2DSolidColorBrush:: ~ CD2DSolidColorBrush](#cd2dsolidcolorbrush__~cd2dsolidcolorbrush)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla pełnego koloru.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSolidColorBrush::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DSolidColorBrush::Create](#create)|Tworzy CD2DSolidColorBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DSolidColorBrush::Destroy](#destroy)|Niszczy obiektu CD2DSolidColorBrush. (Przesłania [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DSolidColorBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DSolidColorBrush::Get](#get)|Zwraca interfejs ID2D1SolidColorBrush|  
|[CD2DSolidColorBrush::GetColor](#getcolor)|Pobiera kolor pędzla pełnego koloru|  
|[CD2DSolidColorBrush::SetColor](#setcolor)|Określa kolor tego pędzla pełnego koloru|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Zwraca interfejs ID2D1SolidColorBrush|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pełny kolor pędzla.|  
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Przechowuje wskaźnika do obiektu ID2D1SolidColorBrush.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dsolidcolorbrush"></a>  CD2DSolidColorBrush:: ~ CD2DSolidColorBrush  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla pełnego koloru.  
  
```  
virtual ~CD2DSolidColorBrush();
```  
  
##  <a name="attach"></a>  CD2DSolidColorBrush::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1SolidColorBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::CD2DSolidColorBrush  
 Tworzy obiekt CD2DSolidColorBrush.  
  
```  
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    D2D1_COLOR_F color,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    COLORREF color,  
    int nAlpha = 255,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `color`  
 Czerwona, zielony, niebieski i alfa wartości kolor pędzla.  
  
 `pBrushProperties`  
 Wskaźnik do nieprzezroczystość i transformacja pędzla.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
 `nAlpha`  
 Nieprzezroczystość kolor pędzla.  
  
##  <a name="create"></a>  CD2DSolidColorBrush::Create  
 Tworzy CD2DSolidColorBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DSolidColorBrush::Destroy  
 Niszczy obiektu CD2DSolidColorBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DSolidColorBrush::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1SolidColorBrush* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DSolidColorBrush::Get  
 Zwraca interfejs ID2D1SolidColorBrush  
  
```  
ID2D1SolidColorBrush* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1SolidColorBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getcolor"></a>  CD2DSolidColorBrush::GetColor  
 Pobiera kolor pędzla pełnego koloru  
  
```  
D2D1_COLOR_F GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor tego pędzla pełnego koloru  
  
##  <a name="m_colorsolid"></a>  CD2DSolidColorBrush::m_colorSolid  
 Pełny kolor pędzla.  
  
```  
D2D1_COLOR_F m_colorSolid;  
```  
  
##  <a name="m_psolidcolorbrush"></a>  CD2DSolidColorBrush::m_pSolidColorBrush  
 Przechowuje wskaźnika do obiektu ID2D1SolidColorBrush.  
  
```  
ID2D1SolidColorBrush* m_pSolidColorBrush;  
```  
  
##  <a name="operator_id2d1solidcolorbrush_star"></a>  CD2DSolidColorBrush::operator ID2D1SolidColorBrush *  
 Zwraca interfejs ID2D1SolidColorBrush  
  
```  
operator ID2D1SolidColorBrush*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1SolidColorBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setcolor"></a>  CD2DSolidColorBrush::SetColor  
 Określa kolor tego pędzla pełnego koloru  
  
```  
void SetColor(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Kolor tego pędzla pełnego koloru  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
