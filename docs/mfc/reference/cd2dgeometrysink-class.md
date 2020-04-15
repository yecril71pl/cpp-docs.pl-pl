---
title: Klasa CD2DGeometrySink
ms.date: 11/04/2016
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
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369240"
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
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Konstruuje obiekt CD2DGeometrySink z obiektu CD2DPathGeometry.|
|[CD2DGeometrySink::~CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destruktor. Wywoływane, gdy obiekt ujścia geometrii D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Dodaje pojedynczy łuk do geometrii ścieżki|
|[CD2DGeometrySink::AddBezier](#addbezier)|Tworzy sześcienną krzywą Beziera między bieżącym punktem a określonym punktem końcowym.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Tworzy sekwencję sześciennych krzywych Beziera i dodaje je do zlewu geometrii.|
|[CD2DGeometrySink::AddLine](#addline)|Tworzy segment linii między bieżącym punktem a określonym punktem końcowym i dodaje go do pochłaniacza geometrii.|
|[CD2DGeometrySink::AddLines](#addlines)|Tworzy sekwencję linii przy użyciu określonych punktów i dodaje je do ujścia geometrii.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Tworzy krzywą kwadratową Beziera między bieżącym punktem a określonym punktem końcowym.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Dodaje sekwencję kwadratowych segmentów Beziera jako tablicy w jednym wywołaniu.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Rozpoczyna nową figurę w określonym punkcie.|
|[CD2DGeometrySink::Zamknij](#close)|Zamyka zlew geometrii|
|[CD2DGeometrySink::EndFigure](#endfigure)|Kończy bieżącą liczbę; opcjonalnie zamyka go.|
|[CD2DGeometrySink::Get](#get)|Zwraca interfejs ID2D1GeometrySink|
|[CD2DGeometrySink::IsValid](#isvalid)|Sprawdza ważność zlewu geometrii|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Określa metodę używaną do określenia, które punkty znajdują się wewnątrz geometrii opisanej przez ten zlew geometrii i które punkty znajdują się na zewnątrz.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Określa opcje obrysu i sprzężenia, które mają być zastosowane do nowych segmentów dodanych do pochłaniacza geometrii.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|Zwraca interfejs ID2D1GeometrySink|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Wskaźnik do ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CD2DGeometrySink`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink::~CD2DGeometrySink

Destruktor. Wywoływane, gdy obiekt ujścia geometrii D2D jest niszczony.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc

Dodaje pojedynczy łuk do geometrii ścieżki

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parametry

*Łuku*<br/>
Segment łuku, który ma być dodawany do rysunku

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier

Tworzy sześcienną krzywą Beziera między bieżącym punktem a określonym punktem końcowym.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Struktura opisująca punkty kontrolne i punkt końcowy krzywej Beziera do dodania.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers

Tworzy sekwencję sześciennych krzywych Beziera i dodaje je do zlewu geometrii.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziers*<br/>
Tablica segmentów Beziera opisująca krzywe Beziera do utworzenia. Krzywa jest rysowana z bieżącego punktu ujścia geometrii (punktu końcowego ostatniego narysowanego segmentu lub lokalizacji określonej przez BeginFigure) do punktu końcowego pierwszego segmentu Beziera w tablicy. jeśli tablica zawiera dodatkowe segmenty Beziera, każdy kolejny segment Beziera używa jako punktu początkowego punktu końcowego poprzedniego segmentu Beziera.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine

Tworzy segment linii między bieżącym punktem a określonym punktem końcowym i dodaje go do pochłaniacza geometrii.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt końcowy linii do rysowania.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines

Tworzy sekwencję linii przy użyciu określonych punktów i dodaje je do ujścia geometrii.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parametry

*Punktów*<br/>
Tablica jednego lub więcej punktów, które opisują wiersze do rysowania. Linia jest rysowana z bieżącego punktu ujścia geometrii (punktu końcowego ostatniego segmentu narysowanego lub lokalizacji określonej przez BeginFigure) do pierwszego punktu w tablicy. jeśli tablica zawiera dodatkowe punkty, linia jest rysowana od pierwszego punktu do drugiego punktu w tablicy, od drugiego punktu do trzeciego punktu i tak dalej. Tablica sekwencji punktów końcowych linii do narysowania.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier

Tworzy krzywą kwadratową Beziera między bieżącym punktem a określonym punktem końcowym.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Struktura opisująca punkt kontrolny i punkt końcowy kwadratowej krzywej Beziera do dodania.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers

Dodaje sekwencję kwadratowych segmentów Beziera jako tablicy w jednym wywołaniu.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziers*<br/>
Tablica sekwencji kwadratowych segmentów Beziera.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure

Rozpoczyna nową figurę w określonym punkcie.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parametry

*Startpoint*<br/>
Punkt, w którym można rozpocząć nową figurę.

*rysunekPoczynić*<br/>
Czy nowa postać powinna być pusta lub wypełniona.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Konstruuje obiekt CD2DGeometrySink z obiektu CD2DPathGeometry.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parametry

*Pathgeometry*<br/>
Istniejący obiekt CD2DPathGeometry.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Zamknij

Zamyka zlew geometrii

```
BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie FALSE.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndFigure

Kończy bieżącą liczbę; opcjonalnie zamyka go.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parametry

*rysunekWykań*<br/>
Wartość wskazująca, czy bieżąca liczba jest zamknięta. Jeśli rysunek jest zamknięty, linia jest rysowana między bieżącym punktem a punktem początkowym określonym przez BeginFigure.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Get

Zwraca interfejs ID2D1GeometrySink

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1GeometrySink lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid

Sprawdza ważność zlewu geometrii

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zlew geometrii jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink

Wskaźnik do ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink*

Zwraca interfejs ID2D1GeometrySink

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1GeometrySink lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::SetFillMode

Określa metodę używaną do określenia, które punkty znajdują się wewnątrz geometrii opisanej przez ten zlew geometrii i które punkty znajdują się na zewnątrz.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parametry

*Fillmode*<br/>
Metoda używana do określenia, czy dany punkt jest częścią geometrii.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags

Określa opcje obrysu i sprzężenia, które mają być zastosowane do nowych segmentów dodanych do pochłaniacza geometrii.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parametry

*wierzchołkiGi*<br/>
Opcje obrysu i sprzężenia, które mają być zastosowane do nowych segmentów dodanych do ujścia geometrii.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
