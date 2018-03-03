---
title: Klasa CD2DGeometrySink | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89286aaccd2c59efb2bac14978a2d8838af7a4e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dgeometrysink-class"></a>Klasa CD2DGeometrySink
Otoka dla ID2D1GeometrySink.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Tworzy obiekt CD2DGeometrySink z CD2DPathGeometry obiektu.|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu sink geometrii D2D.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|Dodaje pojedynczy łuk do geometrii ścieżki.|  
|[CD2DGeometrySink::AddBezier](#addbezier)|Tworzy sześcienny krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego.|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Tworzy sekwencji krzywych Beziera sześcienny i dodaje je do ujścia geometrii.|  
|[CD2DGeometrySink::AddLine](#addline)|Tworzy segmentu linii między bieżącym punktem a określonym punktu końcowego i dodaje go do ujścia geometrii.|  
|[CD2DGeometrySink::AddLines](#addlines)|Tworzy sekwencję wierszy przy użyciu podanych punktów i dodaje je do ujścia geometrii.|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Tworzy kwadratową krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego.|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Dodaje sekwencję kwadratową segmentów Beziera w postaci tablicy w pojedynczym wywołaniu.|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Uruchamia nowe rysunek w określonym momencie.|  
|[CD2DGeometrySink::Close](#close)|Zamyka zbiornika geometrii|  
|[CD2DGeometrySink::EndFigure](#endfigure)|Kończy się bieżący rysunek; Opcjonalnie zamyka go.|  
|[CD2DGeometrySink::Get](#get)|Zwraca interfejs ID2D1GeometrySink|  
|[CD2DGeometrySink::IsValid](#isvalid)|Sprawdza geometrii zbiornika ważności|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Określa metodę używane do określenia, które punkty znajdują się wewnątrz geometrii opisanego przez ten obiekt sink geometry, a które punkty są poza.|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Określa opcje sprzężenia i obrysu ma zostać zastosowany do nowych segmentów dodane do ujścia geometrii.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Zwraca interfejs ID2D1GeometrySink|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|Wskaźnik do ID2D1GeometrySink.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu sink geometrii D2D.  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 Dodaje pojedynczy łuk do geometrii ścieżki.  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>Parametry  
 `arc`  
 Łuku do dodania do rysunku  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 Tworzy sześcienny krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego.  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parametry  
 `bezier`  
 Struktura, która opisuje punktów kontrolnych i krzywej Beziera, aby dodać punkt końcowy.  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 Tworzy sekwencji krzywych Beziera sześcienny i dodaje je do ujścia geometrii.  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parametry  
 `beziers`  
 Tablica segmentów Beziera opisujący krzywych Beziera do utworzenia. Krzywa jest pobierana z obiektu sink geometrii bieżącego punktu (punkt końcowy ostatni segment rysowane lub lokalizacji określonej przez BeginFigure) do punktu końcowego pierwszy segment Beziera w tablicy. Jeśli tablica zawiera dodatkowe segmenty Beziera, każdy z kolejnych segmentów Beziera używa punktu końcowego segmentu Beziera jako jego punkt początkowy.  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 Tworzy segmentu linii między bieżącym punktem a określonym punktu końcowego i dodaje go do ujścia geometrii.  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Punkt końcowy linii do rysowania.  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 Tworzy sekwencję wierszy przy użyciu podanych punktów i dodaje je do ujścia geometrii.  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>Parametry  
 `points`  
 Tablica jeden lub więcej punktów, które opisują wierszy do rysowania. Wiersz jest przenoszony z bieżącego punktu zbiornika geometrii (punkt końcowy ostatni segment rysowane lub lokalizacji określonej przez BeginFigure) do pierwszego punktu w tablicy. Jeśli tablica zawiera dodatkowe punkty, wiersz jest przenoszony z pierwszego punktu do drugiego w tablicy, od drugiego punktu trzeciego punktu i tak dalej. Tablica punktów końcowych wierszy Rysowanie sekwencji.  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 Tworzy kwadratową krzywej Beziera pomiędzy bieżącym punktem a określonym punktu końcowego.  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parametry  
 `bezier`  
 Struktura, która opisuje punkt kontrolny i kwadratową krzywej Beziera, aby dodać punkt końcowy.  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 Dodaje sekwencję kwadratową segmentów Beziera w postaci tablicy w pojedynczym wywołaniu.  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parametry  
 `beziers`  
 Tablica sekwencji kwadratową segmentów Beziera.  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 Uruchamia nowe rysunek w określonym momencie.  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>Parametry  
 `startPoint`  
 Momentu, w którym można rozpocząć nowego rysunku.  
  
 `figureBegin`  
 Określa, czy nowy rysunek powinien być pusty lub wypełniony.  
  
##  <a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 Tworzy obiekt CD2DGeometrySink z CD2DPathGeometry obiektu.  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>Parametry  
 `pathGeometry`  
 Istniejący obiekt CD2DPathGeometry.  
  
##  <a name="close"></a>CD2DGeometrySink::Close  
 Zamyka zbiornika geometrii  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość FALSE.  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 Kończy się bieżący rysunek; Opcjonalnie zamyka go.  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>Parametry  
 `figureEnd`  
 Wartość, która wskazuje, czy bieżący rysunek jest zamknięty. Jeśli rysunek jest zamknięty, między bieżącym punktem a punkt początkowy, określony przez BeginFigure jest rysowana linia.  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 Zwraca interfejs ID2D1GeometrySink  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1GeometrySink lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="isvalid"></a>CD2DGeometrySink::IsValid  
 Sprawdza geometrii zbiornika ważności  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zbiornika geometrii jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 Wskaźnik do ID2D1GeometrySink.  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink *  
 Zwraca interfejs ID2D1GeometrySink  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1GeometrySink lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 Określa metodę używane do określenia, które punkty znajdują się wewnątrz geometrii opisanego przez ten obiekt sink geometry, a które punkty są poza.  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>Parametry  
 `fillMode`  
 Metoda używana do określenia, czy dany punkt jest częścią geometrii.  
  
##  <a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 Określa opcje sprzężenia i obrysu ma zostać zastosowany do nowych segmentów dodane do ujścia geometrii.  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `vertexFlags`  
 Opcje obrysu i sprzężenia ma zostać zastosowany do nowych segmentów dodane do ujścia geometrii.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
