---
title: Klasa CD2DLayer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
dev_langs:
- C++
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 197fc5ecb1b9676dd1ff11327c62950992f6f06d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dlayer-class"></a>Klasa CD2DLayer
Otoka dla ID2D1Layer.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Tworzy obiekt CD2DLayer.|  
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D warstwy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLayer::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DLayer::Create](#create)|Tworzy CD2DLayer. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLayer::Destroy](#destroy)|Niszczy obiektu CD2DLayer. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DLayer::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DLayer::Get](#get)|Zwraca interfejs ID2D1Layer|  
|[CD2DLayer::GetSize](#getsize)|Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia|  
|[CD2DLayer::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|Zwraca interfejs ID2D1Layer|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DLayer::m_pLayer](#m_player)|Przechowuje wskaźnika do obiektu ID2D1Layer.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DLayer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dlayer"></a>  CD2DLayer:: ~ CD2DLayer  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D warstwy.  
  
```  
virtual ~CD2DLayer();
```  
  
##  <a name="attach"></a>  CD2DLayer::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1Layer* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer  
 Tworzy obiekt CD2DLayer.  
  
```  
CD2DLayer(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>  CD2DLayer::Create  
 Tworzy CD2DLayer.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DLayer::Destroy  
 Niszczy obiektu CD2DLayer.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DLayer::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1Layer* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DLayer::Get  
 Zwraca interfejs ID2D1Layer  
  
```  
ID2D1Layer* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Layer lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getsize"></a>  CD2DLayer::GetSize  
 Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia  
  
##  <a name="isvalid"></a>  CD2DLayer::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_player"></a>  CD2DLayer::m_pLayer  
 Przechowuje wskaźnika do obiektu ID2D1Layer.  
  
```  
ID2D1Layer* m_pLayer;  
```  
  
##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer *  
 Zwraca interfejs ID2D1Layer  
  
```  
operator ID2D1Layer* ();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Layer lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
