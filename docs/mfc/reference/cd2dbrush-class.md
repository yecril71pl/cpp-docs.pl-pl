---
title: Klasa CD2DBrush | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 718283893c9e8ec9798dea9a4b9fb307d1099e68
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952060"
---
# <a name="cd2dbrush-class"></a>Klasa CD2DBrush
Otoka dla ID2D1Brush.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Tworzy obiekt CD2DBrush.|  
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBrush::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DBrush::Destroy](#destroy)|Niszczy obiektu CD2DBrush. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DBrush::Get](#get)|Zwraca interfejs ID2D1Brush|  
|[CD2DBrush::GetOpacity](#getopacity)|Pobiera stopień nieprzezroczystości tego pędzla|  
|[CD2DBrush::GetTransform](#gettransform)|Pobiera bieżący transformacji obiektu docelowego renderowania|  
|[CD2DBrush::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DBrush::SetOpacity](#setopacity)|Ustawia maksymalny stopień nieprzezroczystości tego pędzla|  
|[CD2DBrush::SetTransform](#settransform)|Stosuje określona transformacja do obiektu docelowego renderowania, zastępując istniejące transformacji. Wszystkie kolejne operacje rysowania występują w przestrzeni po przekształceniu|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBrush::operator ID2D1Brush *](#operator_id2d1brush_star)|Zwraca interfejs ID2D1Brush|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBrush::m_pBrush](#m_pbrush)|Przechowuje wskaźnika do obiektu ID2D1Brush.|  
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Właściwości pędzla.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBrush`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dbrush"></a>  CD2DBrush:: ~ CD2DBrush  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D pędzla.  
  
```  
virtual ~CD2DBrush();
```  
  
##  <a name="attach"></a>  CD2DBrush::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1Brush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 *pResource*  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush  
 Tworzy obiekt CD2DBrush.  
  
```  
CD2DBrush(
    CRenderTarget* pParentTarget,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Wskaźnik do obiektu docelowego renderowania.  
  
 *pBrushProperties*  
 Wskaźnik do nieprzezroczystość i transformacja pędzla.  
  
 *bAutoDestroy*  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="destroy"></a>  CD2DBrush::Destroy  
 Niszczy obiektu CD2DBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBrush::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1Brush* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DBrush::Get  
 Zwraca interfejs ID2D1Brush  
  
```  
ID2D1Brush* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Brush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getopacity"></a>  CD2DBrush::GetOpacity  
 Pobiera stopień nieprzezroczystości tego pędzla  
  
```  
FLOAT GetOpacity() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od 0 do 1, która wskazuje przezroczystość pędzla. Ta wartość jest mnożnik stałej, która liniowo skaluje alfa wartość wszystkie piksele wypełnił pędzla. Wartość nieprzezroczystości są zablokowane za pomocą w zakresie od 0 do 1 przed są pomnożenie  
  
##  <a name="gettransform"></a>  CD2DBrush::GetTransform  
 Pobiera bieżący transformacji obiektu docelowego renderowania  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *transform*  
 Po powrocie z to zawiera transformacji bieżącego obiektu docelowego renderowania. Ten parametr jest przekazywany jako niezainicjowany  
  
##  <a name="isvalid"></a>  CD2DBrush::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush  
 Przechowuje wskaźnika do obiektu ID2D1Brush.  
  
```  
ID2D1Brush* m_pBrush;  
```  
  
##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties  
 Właściwości pędzla.  
  
```  
CD2DBrushProperties* m_pBrushProperties;  
```  
  
##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::operator ID2D1Brush *  
 Zwraca interfejs ID2D1Brush  
  
```  
operator ID2D1Brush*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Brush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setopacity"></a>  CD2DBrush::SetOpacity  
 Ustawia maksymalny stopień nieprzezroczystości tego pędzla  
  
```  
void SetOpacity(FLOAT opacity);
```  
  
### <a name="parameters"></a>Parametry  
 *Nieprzezroczystość.*  
 Wartość z zakresu od 0 do 1, która wskazuje przezroczystość pędzla. Ta wartość jest mnożnik stałej, która liniowo skaluje alfa wartość wszystkie piksele wypełnił pędzla. Wartość nieprzezroczystości są zablokowane za pomocą w zakresie od 0 do 1 przed są pomnożenie  
  
##  <a name="settransform"></a>  CD2DBrush::SetTransform  
 Stosuje określona transformacja do obiektu docelowego renderowania, zastępując istniejące transformacji. Wszystkie kolejne operacje rysowania występują w przestrzeni po przekształceniu  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>Parametry  
 *transform*  
 Przekształcenie do zastosowania do obiektu docelowego renderowania  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
