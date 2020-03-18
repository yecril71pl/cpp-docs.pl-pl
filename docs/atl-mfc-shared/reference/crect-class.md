---
title: Klasa CRect
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: 13f86c411cca98f5817d1b3b2d9162ae8af8b734
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418252"
---
# <a name="crect-class"></a>Klasa CRect

Podobne do struktury Windows [Rect](/windows/win32/api/windef/ns-windef-rect) .

## <a name="syntax"></a>Składnia

```
class CRect : public tagRECT
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CRect::CRect](#crect)|Konstruuje obiekt `CRect`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Zwraca prawy dolny punkt `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Zwraca Centerpoint `CRect`.|
|[CRect::CopyRect](#copyrect)|Kopiuje wymiary prostokąta źródłowego do `CRect`.|
|[CRect::D eflateRect](#deflaterect)|Zmniejsza szerokość i wysokość `CRect`.|
|[CRect::EqualRect](#equalrect)|Określa, czy `CRect` jest równa danego prostokąta.|
|[CRect:: Height](#height)|Oblicza wysokość `CRect`.|
|[CRect::InflateRect](#inflaterect)|Zwiększa szerokość i wysokość `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Ustawia `CRect` równe przecięcia dwóch prostokątów.|
|[CRect::IsRectEmpty](#isrectempty)|Określa, czy `CRect` jest puste. `CRect` jest puste, jeśli szerokość i/lub wysokość są równe 0.|
|[CRect::IsRectNull](#isrectnull)|Określa, czy zmienne składowe `top`, `bottom`, `left`i `right` są równe 0.|
|[CRect::MoveToX](#movetox)|Przenosi `CRect` do określonej współrzędnej x.|
|[CRect::MoveToXY](#movetoxy)|Przenosi `CRect` do określonych współrzędnych x i y.|
|[CRect:: MoveTo](#movetoy)|Przenosi `CRect` do określonej współrzędnej y.|
|[CRect::NormalizeRect](#normalizerect)|Standaryzacja wysokości i szerokości `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Przenosi `CRect` według określonych przesunięć.|
|[CRect::P tInRect](#ptinrect)|Określa, czy określony punkt leży w `CRect`.|
|[CRect:: SetRect](#setrect)|Ustawia wymiary `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Ustawia `CRect` do pustego prostokąta (wszystkie współrzędne równe 0).|
|[CRect:: size](#size)|Oblicza rozmiar `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Odejmuje jeden prostokąt od innego.|
|[CRect::TopLeft](#topleft)|Zwraca punkt w lewym górnym rogu `CRect`.|
|[CRect::UnionRect](#unionrect)|Ustawia `CRect` równe Unii dwóch prostokątów.|
|[CRect:: Width](#width)|Oblicza szerokość `CRect`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CRect:: operator-](#operator_-)|Odejmuje przesunięcia z `CRect` lub deflate `CRect` i zwraca wynikowy `CRect`.|
|[CRect:: operator LPCRECT](#operator_lpcrect)|Konwertuje `CRect` na `LPCRECT`.|
|[CRect:: operator LPRECT](#operator_lprect)|Konwertuje `CRect` na `LPRECT`.|
|[CRect:: operator! =](#operator_neq)|Określa, czy `CRect` nie jest równa prostokątowi.|
|[CRect:: operator &amp;](#operator_amp)|Tworzy część wspólną `CRect` i prostokąta i zwraca wynikowy `CRect`.|
|[CRect:: operator &amp;=](#operator_amp_eq)|Ustawia `CRect` równe przecięcia `CRect` i prostokąta.|
|[CRect:: operator&#124;](#operator_or)|Tworzy Unię `CRect` i prostokąta i zwraca wynikowy `CRect`.|
|[CRect:: operator &#124;=](#operator_or_eq)|Ustawia `CRect` równe Unii `CRect` i prostokąta.|
|[CRect:: operator +](#operator_add)|Dodaje określone przesunięcia do `CRect` lub niepłaskich `CRect` i zwraca wynikowy `CRect`.|
|[CRect:: operator + =](#operator_add_eq)|Dodaje określone przesunięcia do `CRect` lub niepłaskich `CRect`.|
|[CRect:: operator =](#operator_eq)|Kopiuje wymiary prostokąta do `CRect`.|
|[CRect:: operator-=](#operator_-_eq)|Odejmuje określone przesunięcia od `CRect` lub rozliczeń `CRect`.|
|[CRect:: operator = =](#operator_eq_eq)|Określa, czy `CRect` jest równa prostokątowi.|

## <a name="remarks"></a>Uwagi

`CRect` obejmuje również funkcje elementów członkowskich do manipulowania obiektami `CRect` i strukturą `RECT` systemu Windows.

Obiekt `CRect` można przesłać jako parametr funkcji wszędzie tam, gdzie `RECT` struktura, `LPCRECT`lub `LPRECT`.

> [!NOTE]
> Ta klasa pochodzi od struktury `tagRECT`. (Nazwa `tagRECT` jest mniej często używanej nazwy dla struktury `RECT`). Oznacza to, że członkowie danych (`left`, `top`, `right`i `bottom`) struktury `RECT` są dostępnymi elementami członkowskimi `CRect`.

`CRect` zawiera zmienne składowe, które definiują górny lewy i prawy dolny punkt prostokąta.

Podczas określania `CRect`należy zachować ostrożność, aby skonstruować ją w taki sposób, aby była znormalizowana — innymi słowy, aby wartość lewej współrzędnej była mniejsza od prawej, a górna jest mniejsza niż Dolna. Na przykład w lewym górnym rogu (10, 10) i u dołu z prawej strony (20, 20) definiuje znormalizowany prostokąt, ale u góry z lewej strony (20, 20) i z prawej strony (10, 10) definiuje prostokąt nieznormalizowany. Jeśli prostokąt nie jest znormalizowany, wiele funkcji Członkowskich `CRect` może zwracać nieprawidłowe wyniki. (Zobacz [CRect:: NormalizeRect](#normalizerect) , aby zapoznać się z listą tych funkcji). Przed wywołaniem funkcji wymagającej znormalizowanych prostokątów można znormalizować prostokąty nieznormalizowane, wywołując funkcję `NormalizeRect`.

Należy zachować ostrożność podczas manipulowania `CRect` przy użyciu funkcji [przechwytywania::D ptolp](../../mfc/reference/cdc-class.md#dptolp) i [przechwytywania:: LPtoDP](../../mfc/reference/cdc-class.md#lptodp) . Jeśli tryb mapowania kontekstu wyświetlania jest taki, że zakres y jest ujemny, jak w `MM_LOENGLISH`, wówczas `CDC::DPtoLP` przekształci `CRect` tak, aby jego góra była większa niż Dolna. Funkcje, takie jak `Height` i `Size`, będą zwracały wartości ujemne dla wysokości przekształconych `CRect`, a prostokąt nie będzie znormalizowany.

Gdy używane są przeciążone operatory `CRect`, pierwszy operand musi być `CRect`; drugi może [być strukturą](/windows/win32/api/windef/ns-windef-rect) lub obiektem `CRect`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagRECT`

`CRect`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes. h

##  <a name="bottomright"></a>CRect::BottomRight

Współrzędne są zwracane jako odwołanie do obiektu [CPoint](cpoint-class.md) , który jest zawarty w `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Współrzędne prawego dolnego rogu prostokąta.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można pobrać lub ustawić prawy dolny róg prostokąta. Ustaw narożny za pomocą tej funkcji po lewej stronie operatora przypisania.

### <a name="example"></a>Przykład

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

##  <a name="centerpoint"></a>CRect::CenterPoint

Oblicza Centerpoint `CRect`, dodając lewe i prawe wartości i dzieląc je przez dwa, a następnie dodając wartości górne i dolne i dzieląc je na dwa.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `CPoint`, który jest centerpointem `CRect`.

### <a name="example"></a>Przykład

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

##  <a name="copyrect"></a>CRect::CopyRect

Kopiuje prostokąt `lpSrcRect` do `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt `CRect`, który ma zostać skopiowany.

### <a name="example"></a>Przykład

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

##  <a name="crect"></a>CRect::CRect

Konstruuje obiekt `CRect`.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parametry

*l*<br/>
Określa lewą pozycję `CRect`.

*&*<br/>
Określa początek `CRect`.

*®*<br/>
Określa prawą pozycję `CRect`.

*b*<br/>
Określa dolną `CRect`.

*srcRect*<br/>
Odwołuje się do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) ze współrzędnymi dla `CRect`.

*lpSrcRect*<br/>
Wskazuje strukturę `RECT` ze współrzędnymi `CRect`.

*moment*<br/>
Określa punkt początkowy prostokąta, który ma być skonstruowany. Odnosi się do lewego górnego rogu.

*zmienia*<br/>
Określa przemieszczenie od lewego górnego rogu do prawego dolnego rogu prostokąta, który ma zostać skonstruowany.

*topLeft*<br/>
Określa pozycję `CRect`w lewym górnym rogu.

*bottomRight*<br/>
Określa prawą dolną pozycję `CRect`.

### <a name="remarks"></a>Uwagi

Jeśli nie podano argumentów, `left`, `top`, `right`i składowe `bottom` nie są inicjowane.

Konstruktory `CRect`(`const RECT&`) i `CRect`(`LPCRECT`) wykonują [CopyRect](#copyrect). Inne konstruktory inicjują zmienne składowe obiektu bezpośrednio.

### <a name="example"></a>Przykład

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

##  <a name="deflaterect"></a>CRect::D eflateRect

`DeflateRect` jest rozsunięty `CRect` przez przeniesienie stron na swoje centrum.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Określa liczbę jednostek do skorygowania lewej i prawej strony `CRect`.

*t*<br/>
Określa liczbę jednostek do skorygowania u góry i u dołu `CRect`.

*zmienia*<br/>
[Rozmiar](/windows/win32/api/windef/ns-windef-size) lub [CSize](csize-class.md) , który określa liczbę jednostek do skorygowania `CRect`. Wartość `cx` określa liczbę jednostek do skorygowania lewej i prawej strony, a wartość `cy` określa liczbę jednostek do skorygowania do góry i u dołu.

*lpRect*<br/>
Wskazuje strukturę [prostokąta](/windows/win32/api/windef/ns-windef-rect) lub `CRect`, która określa liczbę jednostek do skorygowania po każdej stronie.

*l*<br/>
Określa liczbę jednostek do skorygowania po lewej stronie `CRect`.

*&*<br/>
Określa liczbę jednostek do skorygowania do góry `CRect`.

*®*<br/>
Określa liczbę jednostek do skorygowania po prawej stronie `CRect`.

*b*<br/>
Określa liczbę jednostek do skorygowania do dołu `CRect`.

### <a name="remarks"></a>Uwagi

Aby to zrobić, `DeflateRect` dodaje jednostki z lewej i góry i odejmuje jednostki od prawej i dołu. Parametry `DeflateRect` są podpisywane wartości; wartości dodatnie skorygowane `CRect` i wartości ujemne wzrosnąmy.

Pierwsze dwa przeciążenia są korygowane z obu par stron `CRect` tak, aby łączna szerokość była mniejsza o dwa razy *x* (lub `cx`), a jego łączna wysokość została obniżona o dwie godziny *y* (lub `cy`). Pozostałe dwa przeciążenia są korygowane po każdej stronie `CRect` niezależnie od innych.

### <a name="example"></a>Przykład

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

##  <a name="equalrect"></a>CRect::EqualRect

Określa, czy `CRect` jest równa danego prostokąta.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje na strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt, który zawiera współrzędne górnego lewego i prawego dolnego prostokąta.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli dwa prostokąty mają te same wartości górne, lewe, dolne i prawe; w przeciwnym razie 0.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

##  <a name="height"></a>CRect:: Height

Oblicza wysokość `CRect`, odejmując górną wartość od wartości dolnej.

```
int Height() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Wysokość `CRect`.

### <a name="remarks"></a>Uwagi

Wynikowa wartość może być ujemna.

> [!NOTE]
>  Prostokąt musi być znormalizowany lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąt przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>CRect::InflateRect

`InflateRect` rozflate `CRect` przez przesuwanie ich stron od centrum.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Określa liczbę jednostek, które mają zostać pożądane po lewej stronie i po prawej stronie `CRect`.

*t*<br/>
Określa liczbę jednostek do podwyższenia górnego i dolnego `CRect`.

*zmienia*<br/>
Rozmiar lub [CSize](csize-class.md) określający liczbę jednostek do [rozbudowanego](/windows/win32/api/windef/ns-windef-size) `CRect`. Wartość `cx` określa liczbę jednostek, które mają zostać podwyższenie i po prawej stronie, a wartość `cy` określa liczbę jednostek, które mają być pogórne i dolne.

*lpRect*<br/>
Wskazuje strukturę [prostokąta](/windows/win32/api/windef/ns-windef-rect) lub `CRect`, która określa liczbę jednostek do rozbudowy każdej strony.

*l*<br/>
Określa liczbę jednostek, która ma zostać poddana lewej stronie `CRect`.

*&*<br/>
Określa liczbę jednostek do podwyższenia poziomu `CRect`.

*®*<br/>
Określa liczbę jednostek, które mają być podłączane po prawej stronie `CRect`.

*b*<br/>
Określa liczbę jednostek do obdzienia dołu `CRect`.

### <a name="remarks"></a>Uwagi

W tym celu `InflateRect` odejmuje jednostki od lewej i górnej i dodaje jednostki z prawej strony i u dołu. Parametry `InflateRect` są podpisywane wartości; wartości dodatnie są rozdęcie `CRect` i wartości ujemne są korygowane.

Pierwsze dwa przeciążenia rozszerą obie pary stron `CRect` tak, aby łączna szerokość była zwiększona o dwa razy *x* (lub `cx`) i jego łączna wysokość została zwiększona o dwa razy *y* (lub `cy`). Pozostałe dwa przeciążenia rozciążą każdą stronę `CRect` niezależnie od innych.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>CRect::IntersectRect

Sprawia, że `CRect` jest równa przecięciu dwóch istniejących prostokątów.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje [strukturę](/windows/win32/api/windef/ns-windef-rect) prostokąta lub obiekt `CRect`, który zawiera prostokąt źródłowy.

*lpRect2*<br/>
Wskazuje strukturę `RECT` lub obiekt `CRect`, który zawiera prostokąt źródłowy.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli część wspólna nie jest pusta; 0, jeśli część wspólna jest pusta.

### <a name="remarks"></a>Uwagi

Część wspólna jest największym prostokątem zawartym w obu prostokątach.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

##  <a name="isrectempty"></a>CRect::IsRectEmpty

Określa, czy `CRect` jest puste.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość różna od zera, jeśli `CRect` jest pusta; 0, jeśli `CRect` nie jest pusty.

### <a name="remarks"></a>Uwagi

Prostokąt jest pusty, jeśli szerokość i/lub wysokość są równe 0 lub negatywnie. Różni się od `IsRectNull`, który określa, czy wszystkie współrzędne prostokąta są równe zero.

> [!NOTE]
>  Prostokąt musi być znormalizowany lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąt przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>CRect::IsRectNull

Określa, czy wartości górnego, lewego, dolnego i prawego `CRect` są równe 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Różna od zera, jeśli `CRect`wartości górnych, lewych, dolnych i prawych są równe 0; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Różni się od `IsRectEmpty`, który określa, czy prostokąt jest pusty.

### <a name="example"></a>Przykład

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>CRect::MoveToX

Wywołaj tę funkcję, aby przenieść prostokąt do bezwzględnej współrzędnej x określonej przez *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Bezwzględna Współrzędna x dla lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>CRect::MoveToXY

Wywołaj tę funkcję, aby przenieść prostokąt do bezwzględnych współrzędnych x i y.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Bezwzględna Współrzędna x dla lewego górnego rogu prostokąta.

*t*<br/>
Bezwzględna Współrzędna y dla lewego górnego rogu prostokąta.

*moment*<br/>
Struktura `POINT`a określająca bezwzględny górny róg prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>CRect:: MoveTo

Wywołaj tę funkcję, aby przenieść prostokąt do bezwzględnej współrzędnej y określonej przez wartość *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parametry

*t*<br/>
Bezwzględna Współrzędna y dla lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>CRect::NormalizeRect

Normalizuje `CRect` tak, aby wysokość i szerokość były dodatnie.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Uwagi

Prostokąt jest znormalizowany dla pozycjonowania z czwartą ćwiartką, który jest zazwyczaj używany przez system Windows do współrzędnych. `NormalizeRect` porównuje wartości górne i dolne i zamienia je, jeśli Górna wartość jest większa od dołu. Podobnie zamienia wartości lewej i prawej, jeśli po lewej stronie jest większy od prawej strony. Ta funkcja jest przydatna podczas rozpatrywania różnych trybów mapowania i odwróconych prostokątów.

> [!NOTE]
> Następujące `CRect` funkcje Członkowskie wymagają znormalizowanych prostokątów, aby działały prawidłowo: [Height](#height), [Width](#width), [size](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operator = =](#operator_eq_eq), operator [! =](#operator_neq), [operator &#124; ](#operator_or), [operator &#124;=](#operator_or_eq), [operator &](#operator_amp)i [operator & =](#operator_amp_eq).

### <a name="example"></a>Przykład

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>CRect::OffsetRect

Przenosi `CRect` według określonych przesunięć.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Określa ilość do przeniesienia w lewo lub w prawo. Aby przenieść z lewej, musi być ujemna.

*t*<br/>
Określa ilość, która ma zostać przeniesiona w górę lub w dół. Wartość musi być ujemna, aby można było ją przenieść w górę.

*moment*<br/>
Zawiera strukturę [punktu](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) określający oba wymiary, według których ma zostać przeniesione.

*zmienia*<br/>
Zawiera strukturę [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize](csize-class.md) określający oba wymiary, według których ma zostać przeniesione.

### <a name="remarks"></a>Uwagi

Przenosi `CRect`*x* jednostek wzdłuż osi x i *y* wzdłuż osi y. Parametry *x* i *y* są podpisywane wartości, dlatego `CRect` można przenieść w lewo lub w prawo, w górę lub w dół.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect:: operator LPCRECT konwertuje `CRect` na [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Uwagi

Korzystając z tej funkcji, nie jest potrzebny operator address-of ( **&** ). Ten operator zostanie automatycznie użyty podczas przekazywania obiektu `CRect` do funkcji, która oczekuje `LPCRECT`.

##  <a name="operator_lprect"></a>CRect:: operator LPRECT

Konwertuje `CRect` na [lpRect](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Uwagi

Korzystając z tej funkcji, nie jest potrzebny operator address-of ( **&** ). Ten operator zostanie automatycznie użyty podczas przekazywania obiektu `CRect` do funkcji, która oczekuje `LPRECT`.

### <a name="example"></a>Przykład

Zobacz przykład dla [CRect:: operator LPCRECT](#operator_lpcrect).

##  <a name="operator_eq"></a>CRect:: operator =

Przypisuje *srcRect* do `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*<br/>
Odwołuje się do prostokąta źródłowego. Może to być [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect:: operator = =

Określa, czy `rect` jest równa `CRect`, porównując współrzędne ich lewego górnego i prawego dolnego rogu.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Odwołuje się do prostokąta źródłowego. Może to być [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="return-value"></a>Wartość zwrócona

Wartość różna od zera, jeśli jest równa; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

##  <a name="operator_neq"></a>CRect:: operator! =

Określa, czy element *Rect* nie jest równy `CRect`, porównując współrzędne ich lewego górnego i prawego dolnego rogu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Odwołuje się do prostokąta źródłowego. Może to być [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="return-value"></a>Wartość zwrócona

Wartość różna od zera, jeśli nie równa się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

##  <a name="operator_add_eq"></a>CRect:: operator + =

Pierwsze dwa przeciążenia przechodzą `CRect` przez określone przesunięcia.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*moment*<br/>
Struktura [punktu](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) , który określa liczbę jednostek do przeniesienia prostokąta.

*zmienia*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize](csize-class.md) , który określa liczbę jednostek do przeniesienia prostokąta.

*lpRect*<br/>
Wskazuje na strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt zawierający liczbę jednostek, które mają być rozbudowane po obu stronach `CRect`.

### <a name="remarks"></a>Uwagi

Wartości *x* i *y* (lub `cx` i `cy`) parametru są dodawane do `CRect`.

Trzecie Przeciążenie jest rozliczane `CRect` przez liczbę jednostek określonych w każdym elemencie członkowskim parametru.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect:: operator-=

Pierwsze dwa przeciążenia przechodzą `CRect` przez określone przesunięcia.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*moment*<br/>
Struktura [punktu](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) , który określa liczbę jednostek do przeniesienia prostokąta.

*zmienia*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize](csize-class.md) , który określa liczbę jednostek do przeniesienia prostokąta.

*lpRect*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt `CRect`, który zawiera liczbę jednostek do skorygowania po każdej stronie `CRect`.

### <a name="remarks"></a>Uwagi

Wartości *x* i *y* (lub `cx` i `cy`) parametru są odejmowane od `CRect`.

Trzecie Przeciążenie jest rozliczane `CRect` przez liczbę jednostek określonych w każdym elemencie członkowskim parametru. Należy zauważyć, że te funkcje przeciążenia, takie jak [DeflateRect](#deflaterect).

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect:: operator &amp;=

Ustawia `CRect` równe przecięcia `CRect` i `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Zawiera [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="remarks"></a>Uwagi

Część wspólna jest największym prostokątem zawartym w obu prostokątach.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

Zobacz przykład dla [CRect:: IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>CRect:: operator &#124;=

Ustawia `CRect` równe Unii `CRect` i `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Zawiera `CRect` lub [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Uwagi

Unia jest najmniejszym prostokątem zawierającym oba prostokąty źródłowe.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect:: operator +

Pierwsze dwa przeciążenia zwracają obiekt `CRect`, który jest równy `CRect` przesunięty przez określone przesunięcia.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*moment*<br/>
Struktura [punktu](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) , który określa liczbę jednostek do przeniesienia wartości zwracanej.

*zmienia*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize](csize-class.md) , który określa liczbę jednostek do przeniesienia wartości zwracanej.

*lpRect*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt `CRect`, który zawiera liczbę jednostek, które mają zostać rozbudowane po każdej stronie wartości zwracanej.

### <a name="return-value"></a>Wartość zwrócona

`CRect` wynikający z przeniesień lub niepłaskich `CRect` według liczby jednostek określonych w parametrze.

### <a name="remarks"></a>Uwagi

Parametry *x* i *y* (lub `cx` i `cy`) parametru są dodawane do pozycji `CRect`.

Trzecie Przeciążenie zwraca nowe `CRect`, które jest równe `CRect` nierównomiernie według liczby jednostek określonych w każdym elemencie członkowskim parametru.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect:: operator-

Pierwsze dwa przeciążenia zwracają obiekt `CRect`, który jest równy `CRect` przesunięty przez określone przesunięcia.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*moment*<br/>
Struktura [punktu](/windows/win32/api/windef/ns-windef-point) lub `CPoint` obiekt, który określa liczbę jednostek do przeniesienia wartości zwracanej.

*zmienia*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub `CSize` obiekt, który określa liczbę jednostek do przeniesienia wartości zwracanej.

*lpRect*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt `CRect`, który zawiera liczbę jednostek do skorygowania po każdej stronie wartości zwracanej.

### <a name="return-value"></a>Wartość zwrócona

`CRect` wynikający z przesunięcia lub rozliczania `CRect` według liczby jednostek określonych w parametrze.

### <a name="remarks"></a>Uwagi

Parametry *x* i *y* (lub `cx` i `cy`) parametru są odejmowane od pozycji `CRect`.

Trzecie Przeciążenie zwraca nową `CRect`, która jest równa `CRect` stałej liczbie jednostek określonych w każdym elemencie członkowskim parametru. Należy zauważyć, że te funkcje przeciążenia takie jak [DeflateRect](#deflaterect), a nie [SubtractRect](#subtractrect).

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect:: operator &amp;

Zwraca `CRect`, która jest częścią przecięcia `CRect` i *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Zawiera [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="return-value"></a>Wartość zwrócona

`CRect` jest częścią wspólną `CRect` i *rect2*.

### <a name="remarks"></a>Uwagi

Część wspólna jest największym prostokątem zawartym w obu prostokątach.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>CRect:: operator&#124;

Zwraca `CRect`, która jest Unią `CRect` i *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Zawiera [prostokąt](/windows/win32/api/windef/ns-windef-rect) lub `CRect`.

### <a name="return-value"></a>Wartość zwrócona

`CRect`, która jest Unią `CRect` i *rect2*.

### <a name="remarks"></a>Uwagi

Unia jest najmniejszym prostokątem zawierającym oba prostokąty.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>CRect::P tInRect

Określa, czy określony punkt leży w `CRect`.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*moment*<br/>
Zawiera strukturę [punktu](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli punkt leży w `CRect`; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Punkt znajduje się w `CRect`, jeśli znajduje się on w lewej lub górnej części lub znajduje się w obrębie wszystkich czterech boków. Punkt po prawej stronie lub u dołu znajduje się na zewnątrz `CRect`.

> [!NOTE]
>  Prostokąt musi być znormalizowany lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąt przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

##  <a name="setrect"></a>CRect:: SetRect

Ustawia wymiary `CRect` do określonych współrzędnych.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa współrzędną x lewego górnego rogu.

*Y1*<br/>
Określa współrzędną y lewego górnego rogu.

*x2*<br/>
Określa współrzędną x w prawym dolnym rogu.

*Y2*<br/>
Określa współrzędną y prawego dolnego rogu.

### <a name="example"></a>Przykład

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect::SetRectEmpty

Sprawia, `CRect` prostokąt o wartości null, ustawiając wszystkie współrzędne na zero.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Przykład

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>CRect:: SIZE

`cx` i `cy` elementy członkowskie wartości zwracanej zawierają wysokość i szerokość `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt [CSize](csize-class.md) , który zawiera rozmiar `CRect`.

### <a name="remarks"></a>Uwagi

Wysokość lub szerokość może być ujemna.

> [!NOTE]
>  Prostokąt musi być znormalizowany lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąt przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>CRect::SubtractRect

Sprawia, że wymiary `CRect` równe odejmowaniu `lpRectSrc2` od `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lpRectSrc1*<br/>
Wskazuje strukturę [Rect](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiektu, z którego ma zostać odjęty prostokąt.

*lpRectSrc2*<br/>
Wskazuje strukturę `RECT` lub obiekt `CRect`, który ma zostać odjęty od prostokąta wskazywanego przez parametr *lpRectSrc1* .

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Odejmowanie to najmniejszy prostokąt, który zawiera wszystkie punkty w *lpRectScr1* , które nie znajdują się w przecięciu *lpRectScr1* i *lpRectScr2*.

Prostokąt określony przez *lpRectSrc1* będzie niezmieniony, jeśli prostokąt określony przez *lpRectSrc2* nie nakłada się całkowicie na prostokąt określony przez *lpRectSrc1* w co najmniej jednym z kierunków x lub y.

Na przykład jeśli *lpRectSrc1* były (10, 10, 100 100) i *lpRectSrc2* były (50, 50, 150 150), prostokąt wskazywany przez *lpRectSrc1* byłby niezmieniony, gdy zwracana jest funkcja. Jeśli *lpRectSrc1* były (10, 10, 100 100) i *lpRectSrc2* były (50, 10, 150 150), jednak prostokąt wskazywany przez *lpRectSrc1* będzie zawierać współrzędne (10, 10, 50 100), gdy zwracana jest funkcja.

`SubtractRect` nie jest taka sama jak [operator-](#operator_-) lub [operator-=](#operator_-_eq). Żaden z tych operatorów nigdy nie wywołuje `SubtractRect`.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

##  <a name="topleft"></a>CRect::TopLeft

Współrzędne są zwracane jako odwołanie do obiektu [CPoint](cpoint-class.md) , który jest zawarty w `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Współrzędne lewego górnego rogu prostokąta.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można pobrać lub ustawić lewy górny róg prostokąta. Ustaw narożny za pomocą tej funkcji po lewej stronie operatora przypisania.

### <a name="example"></a>Przykład

Zobacz przykład dla [CRect:: Centerpoint](#centerpoint).

##  <a name="unionrect"></a>CRect::UnionRect

Sprawia, że wymiary `CRect` są równe Unii dwóch prostokątów źródła.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje obiekt [Rect](/windows/win32/api/windef/ns-windef-rect) lub `CRect`, który zawiera prostokąt źródłowy.

*lpRect2*<br/>
Wskazuje na `RECT` lub `CRect`, który zawiera prostokąt źródłowy.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli Unia nie jest pusta; 0, jeśli Unia jest pusta.

### <a name="remarks"></a>Uwagi

Unia jest najmniejszym prostokątem zawierającym oba prostokąty źródłowe.

System Windows ignoruje wymiary pustego prostokąta. oznacza to, że prostokąt nie ma wysokości lub nie ma szerokości.

> [!NOTE]
>  Oba prostokąty muszą być znormalizowane lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąty przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect:: Width

Oblicza szerokość `CRect`, odejmując lewą wartość od prawej wartości.

```
int Width() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Szerokość `CRect`.

### <a name="remarks"></a>Uwagi

Szerokość może być ujemna.

> [!NOTE]
>  Prostokąt musi być znormalizowany lub ta funkcja może się nie powieść. Możesz wywołać [NormalizeRect](#normalizerect) , aby znormalizować prostokąt przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Zobacz też

[CPoint, klasa](cpoint-class.md)<br/>
[CSize, klasa](csize-class.md)<br/>
[CINANIA](/windows/win32/api/windef/ns-windef-rect)
