---
title: Klasa CD2DGeometry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05bfd912d3c4b6ee8b462775f6919c5fe81cc936
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dgeometry-class"></a>Klasa CD2DGeometry
Otoka dla ID2D1Geometry.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Tworzy obiekt CD2DGeometry.|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu geometrii D2D.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometry::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Łączy tego geometrii z określona Geometria i zapisuje wynik w ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|W tym artykule opisano przecięcia tego geometrii i określona Geometria. Porównanie odbywa się przy użyciu określonej tolerancji spłaszczania.|  
|[CD2DGeometry::ComputeArea](#computearea)|Oblicza obszaru geometrii po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.|  
|[CD2DGeometry::ComputeLength](#computelength)|Oblicza długość geometrii tak, jakby każdy z segmentów zostały wycofane w wierszu.|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Oblicza wektorowe punktu i tangens w określonej odległości wzdłuż geometrii po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.|  
|[CD2DGeometry::Destroy](#destroy)|Niszczy obiektu CD2DGeometry. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DGeometry::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Wskazuje, czy obszar wypełniony przez geometrii zawierałoby określonego punktu określonego określonej tolerancji spłaszczania.|  
|[CD2DGeometry::Get](#get)|Zwraca interfejs ID2D1Geometry|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Pobiera granice geometrii po rozszerzeniami przez określony grubość i styl i przekształcenia przez wskazana macierz matrix.|  
|[CD2DGeometry::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DGeometry::Outline](#outline)|Oblicza konturu geometrii i zapisuje wynik ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](#simplify)|Tworzy uproszczonej wersji geometrię, która zawiera tylko linii i krzywych Beziera sześcienny (opcjonalnie) i zapisuje wynik ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Określa, czy obrysu geometrii zawiera określony punkt danej grubość pociągnięć określony, styl i przekształcenia.|  
|[CD2DGeometry::Tessellate](#tessellate)|Tworzy zestaw trójkąty zawijaniem zegara, które obejmują geometrii po przekształcone, przy użyciu określonej macierzy i spłaszczone przy użyciu określonej tolerancji.|  
|[CD2DGeometry::Widen](#widen)|Rozszerzenie geometrii przez określony obrysu i zapisuje wynik ID2D1SimplifiedGeometrySink po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Zwraca interfejs ID2D1Geometry|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Wskaźnik do ID2D1Geometry.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DGeometry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry:: ~ CD2DGeometry  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu geometrii D2D.  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>  CD2DGeometry::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry  
 Tworzy obiekt CD2DGeometry.  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry  
 Łączy tego geometrii z określona Geometria i zapisuje wynik w ID2D1SimplifiedGeometrySink.  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `inputGeometry`  
 Geometria do łączenia z tym wystąpieniem.  
  
 `combineMode`  
 Typ operację łączenia do wykonania.  
  
 `inputGeometryTransform`  
 Przekształcenie do zastosowania do inputGeometry przed łączenie.  
  
 `geometrySink`  
 Wynik operacji łączenia.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia mają geometrię. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry  
 W tym artykule opisano przecięcia tego geometrii i określona Geometria. Porównanie odbywa się przy użyciu określonej tolerancji spłaszczania.  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `inputGeometry`  
 Geometria do testowania.  
  
 `inputGeometryTransform`  
 Przekształcenie do zastosowania do inputGeometry.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia mają geometrię. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="computearea"></a>  CD2DGeometry::ComputeArea  
 Oblicza obszaru geometrii po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Przekształcenie do zastosowania do tego geometrii przed rozpoczęciem przetwarzania jego obszaru.  
  
 `area`  
 Gdy metoda zwróci wartość, zawiera wskaźnik do obszaru przekształcone, spłaszczoną wersję tego geometrii. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="computelength"></a>  CD2DGeometry::ComputeLength  
 Oblicza długość geometrii tak, jakby każdy z segmentów zostały wycofane w wierszu.  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii przed obliczeniem jego długość.  
  
 `length`  
 Gdy metoda zwróci wartość, zawiera wskaźnik do długości geometrii. W przypadku zamkniętego mają geometrię długość obejmuje segmentu niejawne zamknięcia. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength  
 Oblicza wektorowe punktu i tangens w określonej odległości wzdłuż geometrii po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `length`  
 Odległość wzdłuż geometrii punktu i tangens można znaleźć. Odległość w przypadku mniej następnie 0, ta metoda oblicza pierwszego punktu w geometrii. Jeśli ta odległość jest większa niż długość geometrii, ta metoda oblicza ostatniego punktu w geometrii.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii przed rozpoczęciem obliczanie określony punkt i tangens.  
  
 `point`  
 Lokalizacja w określonej odległości wzdłuż geometrii. Jeśli geometrii jest pusta, ten punkt zawiera NaN jako x i y wartości.  
  
 `unitTangentVector`  
 Gdy metoda zwróci wartość, zawiera wskaźnik do stycznej wektor w określonej odległości wzdłuż geometrii. Jeśli geometrii jest pusta, to wektor zawiera NaN jako x i y wartości. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="destroy"></a>  CD2DGeometry::Destroy  
 Niszczy obiektu CD2DGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DGeometry::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint  
 Wskazuje, czy obszar wypełniony przez geometrii zawierałoby określonego punktu określonego określonej tolerancji spłaszczania.  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Punkt do testowania.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii przed testowanie pod kątem zawierania.  
  
 `contains`  
 Po powrocie z tej metody zawiera wartość logiczna, która ma wartość PRAWDA, jeśli obszar wypełniony przez geometrii zawiera punkt; w przeciwnym razie wartość FALSE. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Liczbowa dokładność, z którym dokładne ścieżka geometryczne i przecięcia ścieżki jest obliczana. Brak wypełnienia o mniej niż tolerancja punktów nadal są traktowane jako wewnątrz. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="get"></a>  CD2DGeometry::Get  
 Zwraca interfejs ID2D1Geometry  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Geometry lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getbounds"></a>  CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds  
 Pobiera granice geometrii po rozszerzeniami przez określony grubość i styl i przekształcenia przez wskazana macierz matrix.  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strokeWidth`  
 Wielkość, przez którą chcesz rozszerzyć geometrii przez używana do malowania konturu jej.  
  
 `strokeStyle`  
 Styl obrysu rozszerzająca geometrii.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii po geometrii jest przekształcana i geometrii zostały malowania.  
  
 `bounds`  
 Po powrocie z tej metody zawiera granice poszerzył geometrii. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia mają geometrię. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="isvalid"></a>  CD2DGeometry::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry  
 Wskaźnik do ID2D1Geometry.  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *  
 Zwraca interfejs ID2D1Geometry  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Geometry lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="outline"></a>  CD2DGeometry::Outline  
 Oblicza konturu geometrii i zapisuje wynik ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Przekształcenie do zastosowania do konturu geometrii.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, do którego jest dołączany konspektu przekształcone geometrii.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="simplify"></a>  CD2DGeometry::Simplify  
 Tworzy uproszczonej wersji geometrię, która zawiera tylko linii i krzywych Beziera sześcienny (opcjonalnie) i zapisuje wynik ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `simplificationOption`  
 Wartość, która określa, czy uproszczony geometrii powinien zawierać krzywych.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii uproszczone.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, do którego jest dołączany uproszczony geometrii.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint  
 Określa, czy obrysu geometrii zawiera określony punkt danej grubość pociągnięć określony, styl i przekształcenia.  
  
```  
BOOL StrokeContainsPoint(
    CD2DPointF point,  
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Punkt, aby sprawdzić zawieranie.  
  
 `strokeWidth`  
 Grubość pociągnięć do zastosowania.  
  
 `strokeStyle`  
 Styl obrysu do zastosowania.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do obrysowane geometrii.  
  
 `contains`  
 Po powrocie z tej metody zawiera wartość logiczna, która jest ustawiona na wartość TRUE, jeśli obrysu geometrii zawiera określony punkt; w przeciwnym razie wartość FALSE. Należy przydzielić magazynu dla tego parametru.  
  
 `flatteningTolerance`  
 Liczbowa dokładność, z którym dokładne ścieżka geometryczne i przecięcia ścieżki jest obliczana. Brak pociągnięcia przez mniej niż tolerancja punktów nadal są traktowane jako wewnątrz. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="tessellate"></a>  CD2DGeometry::Tessellate  
 Tworzy zestaw trójkąty zawijaniem zegara, które obejmują geometrii po przekształcone, przy użyciu określonej macierzy i spłaszczone przy użyciu określonej tolerancji.  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Przekształcenie do zastosowania do tego geometry, lub wartość NULL.  
  
 `tessellationSink`  
 ID2D1TessellationSink, do którego tesselowaną jest dołączony.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
##  <a name="widen"></a>  CD2DGeometry::Widen  
 Rozszerzenie geometrii przez określony obrysu i zapisuje wynik ID2D1SimplifiedGeometrySink po przeprowadzeniu przekształcenia przez wskazana macierz matrix i spłaszczone przy użyciu określonej tolerancji.  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strokeWidth`  
 Wielkość, o którą należy zwiększyć wartość geometrii.  
  
 `strokeStyle`  
 Styl obrysu do zastosowania do geometrii, lub wartość NULL.  
  
 `worldTransform`  
 Przekształcenie do zastosowania do geometrii po jego rozszerzenia.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, do którego jest dołączany poszerzył geometrii.  
  
 `flatteningTolerance`  
 Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale spowodować wolniejszy wykonanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
