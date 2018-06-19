---
title: Klasa CD2DBitmapBrush | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8fb0833fc82895f1f32fb5c93a6e6519bfe119c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354624"
---
# <a name="cd2dbitmapbrush-class"></a>Klasa CD2DBitmapBrush
Otoka dla ID2D1BitmapBrush.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Przeciążone. Tworzy obiekt CD2DBitmapBrush z pliku.|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|Destruktor. Wywoływane, gdy jest niszczony obiektu D2D pędzla mapy bitowej.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmapBrush::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DBitmapBrush::Create](#create)|Tworzy CD2DBitmapBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmapBrush::Destroy](#destroy)|Niszczy obiektu CD2DBitmapBrush. (Przesłania [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DBitmapBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DBitmapBrush::Get](#get)|Zwraca interfejs ID2D1BitmapBrush|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Pobiera źródło mapy bitowej, która używa tego pędzla do rysowania|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Pobiera metodę, za pomocą którego pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Pobiera metodę, za pomocą którego pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Pobiera metodę interpolacji używaną podczas pędzla mapy bitowej jest skalowany lub obracany|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Określa źródło mapy bitowej, który używa tego pędzla do rysowania|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Określa, jak pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Określa, jak pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Określa tryb interpolacji używany, gdy pędzla mapy bitowej jest skalowany lub obracany|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicjuje obiekt|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Zwraca interfejs ID2D1BitmapBrush|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Przechowuje wskaźnik do obiektu CD2DBitmap.|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Przechowuje wskaźnika do obiektu ID2D1BitmapBrush.|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Bitmap właściwości pędzla.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="dtor"></a>  CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 Destruktor. Wywoływane, gdy jest niszczony obiektu D2D pędzla mapy bitowej.  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>  CD2DBitmapBrush::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush  
 Tworzy obiekt CD2DBitmapBrush.  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `pBitmapBrushProperties`  
 Wskaźnik do tryby Rozszerz i tryb interpolacji pędzla mapy bitowej.  
  
 `pBrushProperties`  
 Wskaźnik do nieprzezroczystość i transformacja pędzla.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
 `uiResID`  
 Identyfikatora zasobu zasobu.  
  
 `lpszType`  
 Wskaźnik do zerem ciąg, który zawiera typ zasobu.  
  
 `sizeDest`  
 Rozmiar docelowego mapy bitowej.  
  
 `lpszImagePath`  
 Wskaźnik do zerem ciąg, który zawiera nazwę pliku.  
  
##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit  
 Inicjuje obiekt  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmapBrushProperties`  
 Wskaźnik do właściwości pędzla mapy bitowej.  
  
##  <a name="create"></a>  CD2DBitmapBrush::Create  
 Tworzy CD2DBitmapBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy  
 Niszczy obiektu CD2DBitmapBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBitmapBrush::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DBitmapBrush::Get  
 Zwraca interfejs ID2D1BitmapBrush  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1BitmapBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap  
 Pobiera źródło mapy bitowej, która używa tego pędzla do rysowania  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu CD2DBitmap lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX  
 Pobiera metodę, za pomocą którego pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która określa, jak pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY  
 Pobiera metodę, za pomocą którego pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która określa, jak pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode  
 Pobiera metodę interpolacji używaną podczas pędzla mapy bitowej jest skalowany lub obracany  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Metodę interpolacji używaną podczas pędzla mapy bitowej jest skalowany lub obracany  
  
##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap  
 Przechowuje wskaźnik do obiektu CD2DBitmap.  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush  
 Przechowuje wskaźnika do obiektu ID2D1BitmapBrush.  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties  
 Bitmap właściwości pędzla.  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 Zwraca interfejs ID2D1BitmapBrush  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1BitmapBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap  
 Określa źródło mapy bitowej, który używa tego pędzla do rysowania  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Używane przez pędzla źródła mapy bitowej  
  
##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX  
 Określa, jak pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>Parametry  
 `extendModeX`  
 Wartość, która określa, jak pędzla poziomie Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY  
 Określa, jak pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>Parametry  
 `extendModeY`  
 Wartość, która określa, jak pędzla pionowo Kafelki tych obszarów, które wykraczają poza jego mapy bitowej  
  
##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode  
 Określa tryb interpolacji używany, gdy pędzla mapy bitowej jest skalowany lub obracany  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>Parametry  
 `interpolationMode`  
 Tryb interpolacji używany, gdy pędzla mapy bitowej jest skalowany lub obracany  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
