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
ms.openlocfilehash: 4727f7b1799604001134ee2f4d2d2e1ce6db87fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754787"
---
# <a name="cd2dgeometry-class"></a>Klasa CD2DGeometry

Otoka dla ID2D1Geometria.

## <a name="syntax"></a>Składnia

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometria::CD2DGeometria](#cd2dgeometry)|Konstruuje obiekt CD2DGeometry.|
|[CD2DGeometria::~CD2DGeometria](#_dtorcd2dgeometry)|Destruktor. Wywoływana, gdy obiekt geometrii D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometria::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DGeometria::CombineWithGeometry](#combinewithgeometry)|Łączy tę geometrię z określoną geometrią i przechowuje wynik w ID2D1SimplifiedGeometrySink.|
|[CD2DGeometria::CompareWithGeometry](#comparewithgeometry)|Opisuje przecięcie między tą geometrią a określoną geometrią. Porównanie jest wykonywane przy użyciu określonej tolerancji spłaszczania.|
|[CD2DGeometria::ComputeArea](#computearea)|Oblicza obszar geometrii po jej przekształceniu przez określoną macierz i spłaszczeniu przy użyciu określonej tolerancji.|
|[CD2DGeometria::ComputeLength](#computelength)|Oblicza długość geometrii tak, jakby każdy segment został rozłożony na linię.|
|[CD2DGeometria::ComputePointAtLength](#computepointatlength)|Oblicza wektor punktowy i styczny w określonej odległości wzdłuż geometrii po tym, jak został przekształcony przez określoną macierz i spłaszczony przy użyciu określonej tolerancji.|
|[CD2DGeometria::Destroja](#destroy)|Niszczy obiekt CD2DGeometry. (Zastępuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometria::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DGeometria::FillContainsPoint](#fillcontainspoint)|Wskazuje, czy obszar wypełniony geometrią będzie zawierał określony punkt, biorąc pod uwagę określoną tolerancję spłaszczania.|
|[CD2DGeometria::Pobierz](#get)|Zwraca interfejs ID2D1Geometry|
|[CD2DGeometria::GetBounds](#getbounds)||
|[CD2DGeometria::GetWidenedBounds](#getwidenedbounds)|Pobiera granice geometrii po jej poszerzeniu przez określoną szerokość obrysu i styl i przekształcony przez określoną macierz.|
|[CD2DGeometria::IsValid](#isvalid)|Sprawdza ważność zasobu (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometria::Konspekt](#outline)|Oblicza kontur geometrii i zapisuje wynik do ID2D1SimplifiedGeometrySink.|
|[CD2DGeometria::Uprość](#simplify)|Tworzy uproszczoną wersję geometrii, która zawiera tylko linie i (opcjonalnie) sześcienne krzywe Beziera i zapisuje wynik na ID2D1SimplifiedGeometrySink.|
|[CD2DGeometria::StrokeContainsPoint](#strokecontainspoint)|Określa, czy obrys geometrii zawiera określony punkt, biorąc pod uwagę określoną grubość, styl i przekłęce obrysu.|
|[CD2DGeometria::Tessellate](#tessellate)|Tworzy zestaw trójkątów z raną zgodnie z ruchem wskazówek zegara, które pokrywają geometrię po jej przekształceniu przy użyciu określonej macierzy i spłaszczeniu przy użyciu określonej tolerancji.|
|[CD2DGeometria::Poszerzyć](#widen)|Rozszerza geometrię o określony obrys i zapisuje wynik w ID2D1SimplifiedGeometrySink po jego przekształceniu przez określoną macierz i spłaszczeniu przy użyciu określonej tolerancji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometria::operator ID2D1Geometria*](#operator_id2d1geometry_star)|Zwraca interfejs ID2D1Geometry|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometria::m_pGeometry](#m_pgeometry)|Wskaźnik do ID2D1Geometria.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2DGeometria::~CD2DGeometria

Destruktor. Wywoływana, gdy obiekt geometrii D2D jest niszczony.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2DGeometria::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2DGeometria::CD2DGeometria

Konstruuje obiekt CD2DGeometry.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2DGeometria::CombineWithGeometry

Łączy tę geometrię z określoną geometrią i przechowuje wynik w ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometria*<br/>
Geometria do połączenia z tym wystąpieniem.

*Combinemode*<br/>
Typ operacji kombajnu do wykonania.

*inputGeometryTransform*<br/>
Transformacja do zastosowania do inputGeometry przed połączeniem.

*geometriaSink*<br/>
Wynik operacji kombajnu.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami wielokątnego przybliżenia geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2DGeometria::CompareWithGeometry

Opisuje przecięcie między tą geometrią a określoną geometrią. Porównanie jest wykonywane przy użyciu określonej tolerancji spłaszczania.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometria*<br/>
Geometria do przetestowania.

*inputGeometryTransform*<br/>
Transformacja do zastosowania do inputGeometry.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami wielokątnego przybliżenia geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2DGeometria::ComputeArea

Oblicza obszar geometrii po jej przekształceniu przez określoną macierz i spłaszczeniu przy użyciu określonej tolerancji.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*światTransform*<br/>
Transformacja, aby zastosować do tej geometrii przed obliczeniem jej powierzchni.

*Obszar*<br/>
Gdy ta metoda zwraca, zawiera wskaźnik do obszaru przekształcony, spłaszczone wersji tej geometrii. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2DGeometria::ComputeLength

Oblicza długość geometrii tak, jakby każdy segment został rozłożony na linię.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*światTransform*<br/>
Transformacja stosowana do geometrii przed obliczeniem jej długości.

*Długość*<br/>
Gdy ta metoda zwraca, zawiera wskaźnik do długości geometrii. W przypadku zamkniętych geometrii długość obejmuje niejawny segment zamykający. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2DGeometria::ComputePointAtLength

Oblicza wektor punktowy i styczny w określonej odległości wzdłuż geometrii po tym, jak został przekształcony przez określoną macierz i spłaszczony przy użyciu określonej tolerancji.

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
Odległość wzdłuż geometrii punktu i stycznej do znalezienia. Jeśli ta odległość jest mniejsza niż 0, ta metoda oblicza pierwszy punkt geometrii. Jeśli ta odległość jest większa niż długość geometrii, ta metoda oblicza ostatni punkt geometrii.

*światTransform*<br/>
Transformacja stosowana do geometrii przed obliczeniem określonego punktu i stycznej.

*Punkt*<br/>
Położenie w określonej odległości wzdłuż geometrii. Jeśli geometria jest pusta, ten punkt zawiera NaN jako wartości x i y.

*jednostkaWszczegnnik*<br/>
Gdy ta metoda zwraca, zawiera wskaźnik do wektora stycznej w określonej odległości wzdłuż geometrii. Jeśli geometria jest pusta, ten wektor zawiera NaN jako wartości x i y. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2DGeometria::Destroja

Niszczy obiekt CD2DGeometry.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2DGeometria::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2DGeometria::FillContainsPoint

Wskazuje, czy obszar wypełniony geometrią będzie zawierał określony punkt, biorąc pod uwagę określoną tolerancję spłaszczania.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt do przetestowania.

*światTransform*<br/>
Transformacja stosowana do geometrii przed testowaniem hermetyzacji.

*Zawiera*<br/>
Gdy ta metoda zwraca, zawiera wartość bool, która jest PRAWDA, jeśli obszar wypełniony przez geometrię zawiera punkt; w przeciwnym razie FALSE. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Dokładność numeryczna, z jaką obliczana jest dokładna ścieżka geometryczna i przecięcie ścieżki. Punkty, w których brakuje wypełnienia o mniej niż tolerancja, są nadal uważane za wewnętrzne. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2DGeometria::Pobierz

Zwraca interfejs ID2D1Geometry

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Geometry lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2DGeometria::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parametry

*światTransform*<br/>
*Granice*

### <a name="return-value"></a>Wartość zwracana

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2DGeometria::GetWidenedBounds

Pobiera granice geometrii po jej poszerzeniu przez określoną szerokość obrysu i styl i przekształcony przez określoną macierz.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*udarWidth*<br/>
Ilość, o którą można poszerzyć geometrię, głaszcząc jej kontur.

*strokeStyle (styl obrysu)*<br/>
Styl obrysu, który rozszerza geometrię.

*światTransform*<br/>
Transformacja stosowana do geometrii po przekształceniu geometrii i po obrysowaniu geometrii.

*Granice*<br/>
Gdy ta metoda zwraca, zawiera granice rozszerzonej geometrii. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami wielokątnego przybliżenia geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2DGeometria::IsValid

Sprawdza ważność zasobu

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2DGeometria::m_pGeometry

Wskaźnik do ID2D1Geometria.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2DGeometria::operator ID2D1Geometria*

Zwraca interfejs ID2D1Geometry

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Geometry lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2DGeometria::Konspekt

Oblicza kontur geometrii i zapisuje wynik do ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*światTransform*<br/>
Transformacja stosowana do konturu geometrii.

*geometriaSink*<br/>
ID2D1SimplifiedGeometrySink, do którego dołączany jest kontur przekształcony geometrii.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2DGeometria::Uprość

Tworzy uproszczoną wersję geometrii, która zawiera tylko linie i (opcjonalnie) sześcienne krzywe Beziera i zapisuje wynik na ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*uproszczenieOpoferacja*<br/>
Wartość określająca, czy uproszczona geometria powinna zawierać krzywe.

*światTransform*<br/>
Transformacja stosowana do uproszczonej geometrii.

*geometriaSink*<br/>
ID2D1SimplifiedGeometrySink, do którego dołączona jest uproszczona geometria.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2DGeometria::StrokeContainsPoint

Określa, czy obrys geometrii zawiera określony punkt, biorąc pod uwagę określoną grubość, styl i przekłęce obrysu.

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
Punkt do badania pod kątem hermetyzacji.

*udarWidth*<br/>
Grubość obrysu do zastosowania.

*strokeStyle (styl obrysu)*<br/>
Styl obrysu do zastosowania.

*światTransform*<br/>
Transformacja stosowana do geometrii obrysowej.

*Zawiera*<br/>
Gdy ta metoda zwraca, zawiera wartość logiczną ustawioną na WARTOŚĆ PRAWDA, jeśli obrys geometrii zawiera określony punkt; w przeciwnym razie FALSE. Należy przydzielić magazyn dla tego parametru.

*SpłaszczanieTolerancja*<br/>
Dokładność numeryczna, z jaką obliczana jest dokładna ścieżka geometryczna i przecięcie ścieżki. Punkty, których brakuje obrysu o mniej niż tolerancja, są nadal uważane za wewnętrzne. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2DGeometria::Tessellate

Tworzy zestaw trójkątów z raną zgodnie z ruchem wskazówek zegara, które pokrywają geometrię po jej przekształceniu przy użyciu określonej macierzy i spłaszczeniu przy użyciu określonej tolerancji.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*światTransform*<br/>
Transformacja do zastosowania do tej geometrii lub NULL.

*tesselationSink*<br/>
ID2D1TesselationSink, do którego tessellated jest dołączany.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2DGeometria::Poszerzyć

Rozszerza geometrię o określony obrys i zapisuje wynik w ID2D1SimplifiedGeometrySink po jego przekształceniu przez określoną macierz i spłaszczeniu przy użyciu określonej tolerancji.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*udarWidth*<br/>
Ilość, o którą można poszerzyć geometrię.

*strokeStyle (styl obrysu)*<br/>
Styl obrysu, aby zastosować do geometrii lub NULL.

*światTransform*<br/>
Transformacja stosowana do geometrii po jej poszerzeniu.

*geometriaSink*<br/>
ID2D1SimplifiedGeometrySink, do którego jest dołączana poszerzona geometria.

*SpłaszczanieTolerancja*<br/>
Maksymalna odległość między punktami w wielokątnym przybliżeniu geometrii. Mniejsze wartości dają dokładniejsze wyniki, ale powodują wolniejsze wykonanie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
