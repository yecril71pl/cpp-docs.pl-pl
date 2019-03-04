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
ms.openlocfilehash: 48c88f0b837b2e49e4c87f07a9aa28c16a66c1e3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271206"
---
# <a name="cd2dgeometrysink-class"></a>Klasa CD2DGeometrySink

Otoka ID2D1GeometrySink.

## <a name="syntax"></a>Składnia

```
class CD2DGeometrySink;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Tworzy obiekt CD2DGeometrySink z CD2DPathGeometry obiektu.|
|[CD2DGeometrySink::~CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt sink geometrii D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Dodaje pojedynczego łuk geometrii ścieżki|
|[CD2DGeometrySink::AddBezier](#addbezier)|Tworzy krzywą Beziera trzeciego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Tworzy sekwencję krzywe Beziera trzeciego stopnia i dodaje je do ujścia geometrii.|
|[CD2DGeometrySink::AddLine](#addline)|Tworzy segment linii pomiędzy bieżącym punktem a określonym punktem końcowym i dodaje go do ujścia geometrii.|
|[CD2DGeometrySink::AddLines](#addlines)|Tworzy sekwencję wierszy przy użyciu określonego punktów i dodaje je do ujścia geometrii.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Tworzy krzywą Beziera drugiego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Dodaje sekwencję drugiego stopnia segmentów Beziera w postaci tablicy w jednym wywołaniu.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Uruchamia nowy rysunek w określonym momencie.|
|[CD2DGeometrySink::Close](#close)|Zamyka ujścia geometrii|
|[CD2DGeometrySink::EndFigure](#endfigure)|Kończy bieżący rysunek; Opcjonalnie zamyka te błędy.|
|[CD2DGeometrySink::Get](#get)|Zwraca ID2D1GeometrySink interfejsu|
|[CD2DGeometrySink::IsValid](#isvalid)|Sprawdza ważność ujścia geometrii|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Określa metodę używaną do określenia, które punkty są wewnątrz geometrii opisanego przez ten obiekt sink geometrii, a które punkty są poza.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Określa opcje obrysu i dołączania mają być stosowane do nowych segmentów dodane do ujścia geometrii.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Zwraca ID2D1GeometrySink interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Wskaźnik do ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CD2DGeometrySink`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  CD2DGeometrySink:: ~ CD2DGeometrySink

Destruktor. Wywołuje się, kiedy niszczony jest obiekt sink geometrii D2D.

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

Dodaje pojedynczego łuk geometrii ścieżki

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parametry

*Łuk*<br/>
Łuku do dodania do rysunku

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

Tworzy krzywą Beziera trzeciego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Struktura, która opisuje punkty kontrolne i punkt końcowy krzywej Beziera do dodania.

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

Tworzy sekwencję krzywe Beziera trzeciego stopnia i dodaje je do ujścia geometrii.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Tablica segmentów Beziera opisujący krzywych Beziera do utworzenia. Krzywej pochodzi z bieżącego punktu ujścia geometrii (punkt końcowy ostatni segment rysowania lub lokalizacji określonej przez BeginFigure) do punktu końcowego pierwszy segment Beziera w tablicy. Jeśli tablica zawiera dodatkowe segmentów Beziera, każdy z kolejnych segmentów Beziera używa punktu końcowego segmentu krzywej Beziera jako jego punkt początkowy.

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

Tworzy segment linii pomiędzy bieżącym punktem a określonym punktem końcowym i dodaje go do ujścia geometrii.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt końcowy linii do rysowania.

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

Tworzy sekwencję wierszy przy użyciu określonego punktów i dodaje je do ujścia geometrii.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parametry

*punkty*<br/>
Tablica jednego lub więcej punktów, które opisują wiersze do rysowania. Linia jest rysowana od ujścia geometrii bieżący punkt (punkt końcowy ostatni segment rysowania lub lokalizacji określonej przez BeginFigure) do pierwszego punktu, w tablicy. Jeśli tablica zawiera dodatkowe punkty, od pierwszego punktu jest rysowana linia do drugiego w tablicy, drugi punkt początkowy punkt trzeci i tak dalej. Tablica sekwencji punktów końcowych wierszy do rysowania.

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

Tworzy krzywą Beziera drugiego stopnia pomiędzy bieżącym punktem a określonym punktem końcowym.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Struktura, która opisuje punkt kontrolny i punkt końcowy krzywą Beziera drugiego stopnia w celu dodania.

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

Dodaje sekwencję drugiego stopnia segmentów Beziera w postaci tablicy w jednym wywołaniu.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziera*<br/>
Tablica sekwencji drugiego stopnia segmentów Beziera.

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

Uruchamia nowy rysunek w określonym momencie.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parametry

*startPoint*<br/>
Punkt, od którego należy rozpocząć nowy rysunek.

*figureBegin*<br/>
Czy nowy rysunek powinien być pusty lub wypełniony.

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

Tworzy obiekt CD2DGeometrySink z CD2DPathGeometry obiektu.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parametry

*pathGeometry*<br/>
Istniejący obiekt CD2DPathGeometry.

##  <a name="close"></a>  CD2DGeometrySink::Close

Zamyka ujścia geometrii

```
BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

Kończy bieżący rysunek; Opcjonalnie zamyka te błędy.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parametry

*figureEnd*<br/>
Wartość, która wskazuje, czy bieżący rysunek jest zamknięty. Jeśli rysunek jest zamknięty, linia jest rysowana pomiędzy bieżącym punktem a określonym przez BeginFigure punktu początkowego.

##  <a name="get"></a>  CD2DGeometrySink::Get

Zwraca ID2D1GeometrySink interfejsu

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1GeometrySink lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

Sprawdza ważność ujścia geometrii

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli geometrii ujścia jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

Wskaźnik do ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::operator ID2D1GeometrySink *

Zwraca ID2D1GeometrySink interfejsu

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1GeometrySink lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

Określa metodę używaną do określenia, które punkty są wewnątrz geometrii opisanego przez ten obiekt sink geometrii, a które punkty są poza.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parametry

*fillMode*<br/>
Metoda używana do określenia, czy dany punkt znajduje się część geometrii.

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

Określa opcje obrysu i dołączania mają być stosowane do nowych segmentów dodane do ujścia geometrii.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parametry

*vertexFlags*<br/>
Opcje obrysu i dołączania mają być stosowane do nowych segmentów dodane do ujścia geometrii.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
