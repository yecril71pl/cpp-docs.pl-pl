---
title: Klasa CD2DGeometry
ms.date: 11/04/2016
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
ms.openlocfilehash: 4549b2e7981d5f8493ddf9f24477e75a94ddde8b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271232"
---
# <a name="cd2dgeometry-class"></a>Klasa CD2DGeometry

Otoka ID2D1Geometry.

## <a name="syntax"></a>Składnia

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Tworzy obiekt CD2DGeometry.|
|[CD2DGeometry::~CD2DGeometry](#_dtorcd2dgeometry)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt geometrii D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometry::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Łączy to tworzenie geometrii za określona Geometria i zapisuje wynik w ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|W tym artykule opisano wspólną między tym geometrii i określona Geometria. Porównanie jest wykonywane przy użyciu określonej tolerancji spłaszczania.|
|[CD2DGeometry::ComputeArea](#computearea)|Oblicza obszaru geometrię, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.|
|[CD2DGeometry::ComputeLength](#computelength)|Oblicza długość geometrię, tak, jakby każdy z segmentów zostały rolki w wierszu.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Oblicza wektorowe punktu i tangens w określonej odległości wzdłuż geometrię, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.|
|[CD2DGeometry::Destroy](#destroy)|Niszczy obiekt CD2DGeometry. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Wskazuje, czy obszar uzupełnione przez geometrii zawierałoby określonego punktu określonego określonej tolerancji spłaszczania.|
|[CD2DGeometry::Get](#get)|Zwraca ID2D1Geometry interfejsu|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Pobiera granice geometrii po zostało rozszerzone, styl i grubość określonej i przekształcenia przez określony macierzy.|
|[CD2DGeometry::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Outline](#outline)|Oblicza Geometria konturu i zapisuje wynik ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Simplify](#simplify)|Tworzy uproszczoną wersję geometrię, która zawiera tylko linii i krzywych Beziera sześcienny (opcjonalnie) i zapisuje wynik ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Określa, czy obrysu geometrii zawiera określony punkt danej grubość obrysu określonego, styl i przekształcania.|
|[CD2DGeometry::Tessellate](#tessellate)|Tworzy zestaw trójkąty z ruchem wskazówek zegara rany, które obejmują geometrii po przetransformowaniu, przy użyciu określonej macierzy i spłaszczona za pomocą określonej tolerancji.|
|[CD2DGeometry::Widen](#widen)|Rozszerza się geometrię, określony obrys i zapisuje wynik w ID2D1SimplifiedGeometrySink, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Zwraca ID2D1Geometry interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

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

Destruktor. Wywołuje się, kiedy niszczony jest obiekt geometrii D2D.

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

Tworzy obiekt CD2DGeometry.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

Łączy to tworzenie geometrii za określona Geometria i zapisuje wynik w ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometry*<br/>
Geometria połączyć się z tym wystąpieniem.

*combineMode*<br/>
Typ operacji łączenia do wykonania.

*inputGeometryTransform*<br/>
Przekształcenie do zastosowania do inputGeometry przed łączenie.

*geometrySink*<br/>
Wynik operacji łączenia.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

W tym artykule opisano wspólną między tym geometrii i określona Geometria. Porównanie jest wykonywane przy użyciu określonej tolerancji spłaszczania.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometry*<br/>
Geometria do testowania.

*inputGeometryTransform*<br/>
Przekształcenie do zastosowania do inputGeometry.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

Oblicza obszaru geometrię, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Przekształcenie do zastosowania do tego geometrii przed jego obszar obliczeń.

*Obszar*<br/>
Po powrocie z tej metody zawiera wskaźnik do obszaru przekształcone, spłaszczonych wersję tego geometrii. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

Oblicza długość geometrię, tak, jakby każdy z segmentów zostały rolki w wierszu.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Przekształcenie do zastosowania do geometrii przed obliczeniem jego długość.

*Długość*<br/>
Po powrocie z tej metody zawiera wskaźnik do długości geometrii. W przypadku zamknięte geometrii długość obejmuje segmentu niejawne zamknięcia. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

Oblicza wektorowe punktu i tangens w określonej odległości wzdłuż geometrię, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Odległość wzdłuż geometrii punktu i tangens można znaleźć. Jeśli jest to mniej następnie 0, ta metoda oblicza pierwszy punkt geometrii. Jeśli to jest większa niż długość geometrię, ta metoda oblicza ostatniego punktu w geometrii.

*worldTransform*<br/>
Przekształcenie do zastosowania do geometrii przed obliczeniem określony punkt i tangensa.

*Punkt*<br/>
Lokalizacja w określonej odległości wzdłuż geometrii. Jeśli geometrii jest pusta, ten punkt zawiera NaN w postaci współrzędnych x i y wartości.

*unitTangentVector*<br/>
Po powrocie z tej metody zawiera wskaźnik do funkcji tangens wektora w określonej odległości wzdłuż geometrii. Jeśli geometrii jest pusty, ta wektor zawiera NaN jako współrzędnych x i y wartości. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="destroy"></a>  CD2DGeometry::Destroy

Niszczy obiekt CD2DGeometry.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

Wskazuje, czy obszar uzupełnione przez geometrii zawierałoby określonego punktu określonego określonej tolerancji spłaszczania.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt do testowania.

*worldTransform*<br/>
Przekształcenie do zastosowania do geometrii przed testowanie pod kątem zawierania.

*zawiera*<br/>
Po powrocie z tej metody zawiera wartość logiczna, która ma wartość TRUE, jeśli obszar uzupełnione przez geometrii zawiera punkt; w przeciwnym razie wartość FALSE. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Dokładność liczbowych, za pomocą którego dokładny ścieżki geometrycznej i wspólną ścieżki jest obliczana. Brak wypełnienie przez mniej niż tolerancja punkty są nadal uważane za wewnątrz. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="get"></a>  CD2DGeometry::Get

Zwraca ID2D1Geometry interfejsu

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

*worldTransform*<br/>
*Granice*

### <a name="return-value"></a>Wartość zwracana

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

Pobiera granice geometrii po zostało rozszerzone, styl i grubość określonej i przekształcenia przez określony macierzy.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*strokeWidth*<br/>
Wielkość, przez którą chcesz rozszerzyć geometrii przez stykają konturu jej.

*strokeStyle*<br/>
Styl obrysu rozszerzająca geometrii.

*worldTransform*<br/>
Przekształcenie do zastosowania do geometrii po geometrii jest przekształcane i geometrii zostały malowania.

*Granice*<br/>
Po powrocie z tej metody zawiera granice poszerzył geometrii. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

Wskaźnik do ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *

Zwraca ID2D1Geometry interfejsu

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Geometry lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="outline"></a>  CD2DGeometry::Outline

Oblicza Geometria konturu i zapisuje wynik ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Przekształcenie do zastosowania do konturu geometrii.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, do którego jest dołączany Geometria konturu przekształcone.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="simplify"></a>  CD2DGeometry::Simplify

Tworzy uproszczoną wersję geometrię, która zawiera tylko linii i krzywych Beziera sześcienny (opcjonalnie) i zapisuje wynik ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*simplificationOption*<br/>
Wartość, która określa, czy uproszczona geometrii powinien zawierać krzywych.

*worldTransform*<br/>
Przekształcenie do zastosowania do uproszczonego geometrii.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, do którego jest dołączany uproszczone geometrii.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

Określa, czy obrysu geometrii zawiera określony punkt danej grubość obrysu określonego, styl i przekształcania.

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

*Punkt*<br/>
Punkt, aby sprawdzić zawieranie.

*strokeWidth*<br/>
Grubość obrysu do zastosowania.

*strokeStyle*<br/>
Styl obrysu do zastosowania.

*worldTransform*<br/>
Przekształcenie do zastosowania do obrysowane geometrii.

*zawiera*<br/>
Po powrocie z tej metody zawiera wartość logiczna, która jest ustawiona na wartość TRUE, jeśli obrysu geometrii zawiera określony punkt; w przeciwnym razie wartość FALSE. Należy przydzielić pamięci masowej dla tego parametru.

*flatteningTolerance*<br/>
Dokładność liczbowych, za pomocą którego dokładny ścieżki geometrycznej i wspólną ścieżki jest obliczana. Brak pociągnięcia przez mniej niż tolerancja punkty są nadal uważane za wewnątrz. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

Tworzy zestaw trójkąty z ruchem wskazówek zegara rany, które obejmują geometrii po przetransformowaniu, przy użyciu określonej macierzy i spłaszczona za pomocą określonej tolerancji.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Przekształcenie do zastosowania do tego geometry, lub wartość NULL.

*tessellationSink*<br/>
ID2D1TessellationSink, do którego tesselowaną jest dołączany.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="widen"></a>  CD2DGeometry::Widen

Rozszerza się geometrię, określony obrys i zapisuje wynik w ID2D1SimplifiedGeometrySink, po przeprowadzeniu przekształcone w określonej macierzy i spłaszczona za pomocą określonej tolerancji.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*strokeWidth*<br/>
Kwota za pomocą którego można poszerzyć geometrii.

*strokeStyle*<br/>
Styl obrysu mające zastosowanie do geometrii, lub wartość NULL.

*worldTransform*<br/>
Przekształcenie do zastosowania do geometrii po jego rozszerzenia.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, do którego jest dołączany poszerzył geometrii.

*flatteningTolerance*<br/>
Granice maksymalną odległość między punktami w wielokątne zbliżenia geometrii. Mniejsze wartości pozwalają uzyskać dokładniejsze wyniki, ale powodować wolniejsze wykonywania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
