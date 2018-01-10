---
title: Klasa CD2DLinearGradientBrush | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
dev_langs: C++
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19c060c846d8dfd12a8b783f0b01153c9a424cfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dlineargradientbrush-class"></a>Klasa CD2DLinearGradientBrush
Otoka dla ID2D1LinearGradientBrush.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Tworzy obiekt CD2DLinearGradientBrush.|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla gradientu liniowego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DLinearGradientBrush::Create](#create)|Tworzy CD2DLinearGradientBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|Niszczy obiektu CD2DLinearGradientBrush. (Przesłania [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DLinearGradientBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DLinearGradientBrush::Get](#get)|Zwraca interfejs ID2D1LinearGradientBrush|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Pobiera końcowy współrzędne gradientu liniowego|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Pobiera początkowy współrzędne gradientu liniowego|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Ustawia współrzędne końcowy gradientu liniowego w przestrzeni współrzędnych pędzla|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Ustawia współrzędne początkowego gradientu liniowego w przestrzeni współrzędnych pędzla|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Zwraca interfejs ID2D1LinearGradientBrush|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Punkt początkowy i końcowy gradientu.|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Wskaźnik do ID2D1LinearGradientBrush.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla gradientu liniowego.  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="attach"></a>CD2DLinearGradientBrush::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush  
 Tworzy obiekt CD2DLinearGradientBrush.  
  
```  
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `gradientStops`  
 Wskaźnik do tablicy D2D1_GRADIENT_STOP struktury.  
  
 `gradientStopsCount`  
 Wartość większa niż lub równa 1, która określa liczbę gradientu w tablicy gradientStops.  
  
 `LinearGradientBrushProperties`  
 Punkt początkowy i końcowy gradientu.  
  
 `colorInterpolationGamma`  
 Miejsca, w których kolor jest wykonywane interpolacji między gradientu.  
  
 `extendMode`  
 Zachowanie gradientu poza zakresem znormalizowane [0,1].  
  
 `pBrushProperties`  
 Wskaźnik do nieprzezroczystość i transformacja pędzla.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>CD2DLinearGradientBrush::Create  
 Tworzy CD2DLinearGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>CD2DLinearGradientBrush::Destroy  
 Niszczy obiektu CD2DLinearGradientBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLinearGradientBrush::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>CD2DLinearGradientBrush::Get  
 Zwraca interfejs ID2D1LinearGradientBrush  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1LinearGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint  
 Pobiera końcowy współrzędne gradientu liniowego  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Końcowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla  
  
##  <a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint  
 Pobiera początkowy współrzędne gradientu liniowego  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Początkowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla  
  
##  <a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 Punkt początkowy i końcowy gradientu.  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush  
 Wskaźnik do ID2D1LinearGradientBrush.  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *  
 Zwraca interfejs ID2D1LinearGradientBrush  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1LinearGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint  
 Ustawia współrzędne końcowy gradientu liniowego w przestrzeni współrzędnych pędzla  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Końcowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla  
  
##  <a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint  
 Ustawia współrzędne początkowego gradientu liniowego w przestrzeni współrzędnych pędzla  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Początkowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
