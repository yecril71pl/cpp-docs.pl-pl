---
title: Klasa CD2DPathGeometry | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs: C++
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9142b268c5f09a88883d048c35287966d9ef8aab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpathgeometry-class"></a>Klasa CD2DPathGeometry
Otoka dla ID2D1PathGeometry.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Tworzy obiekt CD2DPathGeometry.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DPathGeometry::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DPathGeometry::Create](#create)|Tworzy CD2DPathGeometry. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DPathGeometry::Destroy](#destroy)|Niszczy obiektu CD2DPathGeometry. (Przesłania [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|  
|[CD2DPathGeometry::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Pobiera liczbę cyfr geometrii ścieżki.|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Pobiera liczbę segmentów ścieżki geometrii.|  
|[CD2DPathGeometry::Open](#open)|Pobiera zbiornika geometry, używany do wypełniania geometrii ścieżki z rysunki i segmentów.|  
|[CD2DPathGeometry::Stream](#stream)|Kopiuje zawartość geometrii ścieżki do określonego ID2D1GeometrySink.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Wskaźnik do ID2D1PathGeometry.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="attach"></a>CD2DPathGeometry::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry  
 Tworzy obiekt CD2DPathGeometry.  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>CD2DPathGeometry::Create  
 Tworzy CD2DPathGeometry.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>CD2DPathGeometry::Destroy  
 Niszczy obiektu CD2DPathGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DPathGeometry::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount  
 Pobiera liczbę cyfr geometrii ścieżki.  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wartości geometrii ścieżki.  
  
##  <a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount  
 Pobiera liczbę segmentów ścieżki geometrii.  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę segmentów ścieżki geometrii.  
  
##  <a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry  
 Wskaźnik do ID2D1PathGeometry.  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>CD2DPathGeometry::Open  
 Pobiera zbiornika geometry, używany do wypełniania geometrii ścieżki z rysunki i segmentów.  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ID2D1GeometrySink, używany do wypełniania geometrii ścieżki z rysunki i segmentów.  
  
##  <a name="stream"></a>CD2DPathGeometry::Stream  
 Kopiuje zawartość geometrii ścieżki do określonego ID2D1GeometrySink.  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>Parametry  
 `geometrySink`  
 Obiekt sink, do której są kopiowane zawartość geometrii ścieżki. Zmodyfikowanie ten obiekt sink nie zmienia się zawartość geometrii tej ścieżki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
