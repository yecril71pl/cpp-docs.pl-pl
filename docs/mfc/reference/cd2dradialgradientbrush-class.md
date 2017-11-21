---
title: Klasa CD2DRadialGradientBrush | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
dev_langs: C++
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a190bbe75a7b0d0f26d210e299d58e8b6ba6caa7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cd2dradialgradientbrush-class"></a>Klasa CD2DRadialGradientBrush
Otoka dla ID2D1RadialGradientBrush.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Tworzy obiekt CD2DLinearGradientBrush.|  
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla gradientu promieniowego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DRadialGradientBrush::Create](#create)|Tworzy CD2DRadialGradientBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DRadialGradientBrush::Destroy](#destroy)|Niszczy obiektu CD2DRadialGradientBrush. (Przesłania [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DRadialGradientBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DRadialGradientBrush::Get](#get)|Zwraca interfejs ID2D1RadialGradientBrush|  
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Pobiera Centrum elipsy gradientu|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Pobiera przesunięcia początkowego gradientu względem Centrum elipsy gradientu|  
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Pobiera promień x elipsy gradientu|  
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Pobiera promień y elipsy gradientu|  
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Określa Centrum gradientu elipsy w przestrzeni współrzędnych pędzla|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Określa przesunięcie punktu początkowego gradientu względem elipsy gradientu Centrum|  
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla|  
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Zwraca interfejs ID2D1RadialGradientBrush|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Wskaźnik do ID2D1RadialGradientBrush.|  
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Centrum, przesunięcie początek gradientu i x radius i y-radius pędzla przez gradientu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DRadialGradientBrush`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla gradientu promieniowego.  
  
```  
virtual ~CD2DRadialGradientBrush();
```  
  
##  <a name="attach"></a>CD2DRadialGradientBrush::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1RadialGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush  
 Tworzy obiekt CD2DLinearGradientBrush.  
  
```  
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,  
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
  
 `RadialGradientBrushProperties`  
 Centrum, przesunięcie początek gradientu i x radius i y-radius pędzla przez gradientu.  
  
 `colorInterpolationGamma`  
 Miejsca, w których kolor jest wykonywane interpolacji między gradientu.  
  
 `extendMode`  
 Zachowanie gradientu poza zakresem znormalizowane [0,1].  
  
 `pBrushProperties`  
 Wskaźnik do nieprzezroczystość i transformacja pędzla.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>CD2DRadialGradientBrush::Create  
 Tworzy CD2DRadialGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>CD2DRadialGradientBrush::Destroy  
 Niszczy obiektu CD2DRadialGradientBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DRadialGradientBrush::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1RadialGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>CD2DRadialGradientBrush::Get  
 Zwraca interfejs ID2D1RadialGradientBrush  
  
```  
ID2D1RadialGradientBrush* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1RadialGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter  
 Pobiera Centrum elipsy gradientu  
  
```  
CD2DPointF GetCenter() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Centrum elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla  
  
##  <a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset  
 Pobiera przesunięcia początkowego gradientu względem Centrum elipsy gradientu  
  
```  
CD2DPointF GetGradientOriginOffset() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przesunięcie punktu początkowego gradientu od środka elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla  
  
##  <a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX  
 Pobiera promień x elipsy gradientu  
  
```  
FLOAT GetRadiusX() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Promień x elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla  
  
##  <a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY  
 Pobiera promień y elipsy gradientu  
  
```  
FLOAT GetRadiusY() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Promień y elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla  
  
##  <a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush  
 Wskaźnik do ID2D1RadialGradientBrush.  
  
```  
ID2D1RadialGradientBrush* m_pRadialGradientBrush;  
```  
  
##  <a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties  
 Centrum, przesunięcie początek gradientu i x radius i y-radius pędzla przez gradientu.  
  
```  
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;  
```  
  
##  <a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *  
 Zwraca interfejs ID2D1RadialGradientBrush  
  
```  
operator ID2D1RadialGradientBrush*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1RadialGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter  
 Określa Centrum gradientu elipsy w przestrzeni współrzędnych pędzla  
  
```  
void SetCenter(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Centrum gradientu elipsy, w przestrzeni współrzędnych pędzla  
  
##  <a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset  
 Określa przesunięcie punktu początkowego gradientu względem elipsy gradientu Centrum  
  
```  
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```  
  
### <a name="parameters"></a>Parametry  
 `gradientOriginOffset`  
 Przesunięcie punktu początkowego gradientu od środka elipsy gradientu  
  
##  <a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX  
 Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla  
  
```  
void SetRadiusX(FLOAT radiusX);
```  
  
### <a name="parameters"></a>Parametry  
 `radiusX`  
 Promień x elipsy gradientu. Ta wartość jest w przestrzeni współrzędnych pędzla  
  
##  <a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY  
 Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla  
  
```  
void SetRadiusY(FLOAT radiusY);
```  
  
### <a name="parameters"></a>Parametry  
 `radiusY`  
 Promień y elipsy gradientu. Ta wartość jest w przestrzeni współrzędnych pędzla  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
