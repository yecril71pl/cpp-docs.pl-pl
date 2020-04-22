---
title: CRect, klasa
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
ms.openlocfilehash: b99eca7fe3a9c84f8b79ef3d694e27b6dd74dcd9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747054"
---
# <a name="crect-class"></a>CRect, klasa

Podobnie jak w strukturze [RECT](/windows/win32/api/windef/ns-windef-rect) systemu Windows.

## <a name="syntax"></a>Składnia

```
class CRect : public tagRECT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::CRect](#crect)|Konstruuje `CRect` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Zwraca prawy dolny `CRect`punkt .|
|[CRect::CenterPoint](#centerpoint)|Zwraca punkt środkowy `CRect`.|
|[CRect::CopyRect](#copyrect)|Kopiuje wymiary prostokąta źródłowego do `CRect`pliku .|
|[CRect::DeflateRect](#deflaterect)|Zmniejsza szerokość i wysokość `CRect`.|
|[CRect::Equalrect](#equalrect)|Określa, `CRect` czy jest równa danego prostokąta.|
|[CRect::Wysokość](#height)|Oblicza wysokość `CRect`.|
|[CRect::InflateRect](#inflaterect)|Zwiększa szerokość i `CRect`wysokość .|
|[CRect::IntersectRect](#intersectrect)|Zestawy `CRect` równe przecięciu dwóch prostokątów.|
|[CRect::IsRectEmpty](#isrectempty)|Określa, `CRect` czy jest pusty. `CRect`jest pusta, jeśli szerokość i/lub wysokość to 0.|
|[CRect::Isrectnull](#isrectnull)|`top`Określa, czy `bottom`zmienne , `left`, i `right` element członkowski są równe 0.|
|[CRect::MoveToX](#movetox)|Przechodzi `CRect` do określonej współrzędnej x.|
|[CRect::MoveToXY](#movetoxy)|Przenosi `CRect` do określonych współrzędnych x- i y.|
|[CRect::MoveToY](#movetoy)|Przechodzi `CRect` do określonej współrzędnej y.|
|[CRect::NormalizeRect](#normalizerect)|Standaryzuje wysokość i `CRect`szerokość .|
|[CRect::OffsetRect](#offsetrect)|Przenosi `CRect` się przez określone odsunięcia.|
|[CRect::PtInRect](#ptinrect)|Określa, czy określony punkt `CRect`znajduje się w obrębie .|
|[CRect::SetRect](#setrect)|Ustawia wymiary `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Ustawia `CRect` pusty prostokąt (wszystkie współrzędne równe 0).|
|[CRect::Rozmiar](#size)|Oblicza rozmiar `CRect`pliku .|
|[CRect::OdejmowanieWyczyciek](#subtractrect)|Odejmuje jeden prostokąt od drugiego.|
|[CRect::TopLeft](#topleft)|Zwraca lewy górny `CRect`punkt .|
|[CRect::UnionRect](#unionrect)|Zestawy `CRect` równe unii dwóch prostokątów.|
|[CRect::Szerokość](#width)|Oblicza szerokość `CRect`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::operator -](#operator_-)|Odejmuje podane odsunięcia lub `CRect` opróżnia `CRect` i zwraca wynikowy `CRect`.|
|[CRect::operator LPCRECT](#operator_lpcrect)|Konwertuje `CRect` a `LPCRECT`do .|
|[CRect::operator LPRECT](#operator_lprect)|Konwertuje `CRect` a `LPRECT`do .|
|[CRect::operator !=](#operator_neq)|Określa, `CRect` czy nie jest równa prostokąt.|
|[CRect::operator&amp;](#operator_amp)|Tworzy przecięcie `CRect` i prostokąt i zwraca `CRect`wynikowy .|
|[CRect::operator&amp;=](#operator_amp_eq)|Ustawia `CRect` równe przecięciu `CRect` i prostokątowi.|
|[CRect::operator &#124;](#operator_or)|Tworzy połączenie `CRect` i prostokąt i zwraca wynikowy `CRect`.|
|[CRect::operator &#124;=](#operator_or_eq)|Zestawy `CRect` równe unii `CRect` i prostokąta.|
|[CRect::operator +](#operator_add)|Dodaje podane przesunięcia `CRect` `CRect` do lub zawyża i zwraca wynikowy `CRect`.|
|[CRect::operator +=](#operator_add_eq)|Dodaje określone odsunięcia `CRect` `CRect`do lub zawyża .|
|[CRect::operator =](#operator_eq)|Kopiuje wymiary prostokąta `CRect`do .|
|[CRect::operator -=](#operator_-_eq)|Odejmuje określone odsunięcia lub `CRect` opróżnia `CRect`.|
|[CRect::operator ==](#operator_eq_eq)|Określa, `CRect` czy jest równa prostokąt.|

## <a name="remarks"></a>Uwagi

`CRect`zawiera również funkcje `CRect` członkowskie do `RECT` manipulowania obiektami i strukturami systemu Windows.

Obiekt `CRect` może być przekazywany jako `RECT` parametr `LPCRECT`funkcji `LPRECT` wszędzie tam, gdzie struktura , lub mogą być przekazywane.

> [!NOTE]
> Ta klasa jest pochodną `tagRECT` struktury. (Nazwa `tagRECT` jest rzadziej używaną nazwą `RECT` struktury). Oznacza to, że`left`elementy `top` `right`członkowskie `bottom`danych ( `RECT` , , , `CRect`i ) struktury są dostępne elementy członkowskie danych .

A `CRect` zawiera zmienne członkowskie definiujące lewy górny i prawy dolny r. punkt prostokąta.

Podczas określania `CRect`, należy uważać, aby skonstruować go tak, aby był znormalizowany — innymi słowy, tak, że wartość lewej współrzędnej jest mniejsza niż po prawej stronie, a górna jest mniejsza niż dolna. Na przykład w lewym górnym rogu (10,10) i prawym dolnym rogu (20,20) definiuje znormalizowany prostokąt, ale w lewym górnym rogu (20,20) i prawym dolnym (10,10) definiuje prostokąt nieznormalizowany. Jeśli prostokąt nie jest znormalizowany, wiele `CRect` funkcji członkowskich może zwrócić nieprawidłowe wyniki. (Zobacz [CRect::NormalizeRect](#normalizerect) dla listy tych funkcji.) Przed wywołaniem funkcji, która wymaga znormalizowanych prostokątów, można normalizować nieznormizowane prostokąty, wywołując `NormalizeRect` funkcję.

Należy zachować ostrożność `CRect` podczas manipulowania za pomocą funkcji elementów członkowskich [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) i [CDC::LPtoDP.](../../mfc/reference/cdc-class.md#lptodp) Jeśli tryb mapowania kontekstu wyświetlania jest taki, że zakres `MM_LOENGLISH`y jest ujemny, jak w , następnie `CDC::DPtoLP` przekształci `CRect` się tak, aby jego górna część była większa niż dolna. Funkcje, `Height` `Size` takie jak i zwróci wartości ujemne dla wysokości przekształcony `CRect`, a prostokąt nie będzie znormalizowane.

W przypadku korzystania `CRect` z przeciążonych operatorów `CRect`pierwszy operand musi być ; drugi może być strukturą [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect` lub obiektem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagRECT`

`CRect`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::BottomRight

Współrzędne są zwracane jako odwołanie do obiektu `CRect` [CPoint,](cpoint-class.md) który znajduje się w programie .

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Współrzędne prawego dolnego rogu prostokąta.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można uzyskać lub ustawić prawy dolny róg prostokąta. Ustaw narożnik, używając tej funkcji po lewej stronie operatora przypisania.

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::CenterPoint

Oblicza punkt `CRect` środkowy, dodając wartości lewe i prawe i dzieląc przez dwa, dodając górne i dolne wartości i dzieląc przez dwa.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CPoint` który jest punktem środkowym pliku `CRect`.

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

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::CopyRect

Kopiuje `lpSrcRect` prostokąt do `CRect`pliku .

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parametry

*lpSrcrect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt, który ma zostać skopiowany.

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

## <a name="crectcrect"></a><a name="crect"></a>CRect::CRect

Konstruuje `CRect` obiekt.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parametry

*L*<br/>
Określa pozycję po `CRect`lewej stronie .

*t*<br/>
Określa górną `CRect`część pliku .

*R*<br/>
Określa właściwą pozycję `CRect`.

*B*<br/>
Określa dolną `CRect`część pliku .

*srcRect*<br/>
Odnosi się do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) ze `CRect`współrzędnymi dla .

*lpSrcrect*<br/>
Wskazuje na `RECT` strukturę ze `CRect`współrzędnymi dla .

*Punkt*<br/>
Określa punkt początkowy prostokąta, który ma zostać skonstruowany. Odpowiada lewemu górnemu narożnikowi.

*Rozmiar*<br/>
Określa przemieszczenie od lewego górnego rogu do prawego dolnego rogu prostokąta, który ma zostać skonstruowany.

*topLeft*<br/>
Określa pozycję w lewym `CRect`górnym rogu .

*bottomRight*<br/>
Określa pozycję w prawym `CRect`dolnym rogu .

### <a name="remarks"></a>Uwagi

Jeśli nie podano `left`żadnych `top` `right`argumentów `bottom` , , i elementy członkowskie nie są inicjowane.

`CRect`Konstruktory `CRect``LPCRECT`(`const RECT&`) i ( ) wykonują [CopyRect](#copyrect). Inne konstruktory inicjują zmienne członkowskie obiektu bezpośrednio.

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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::DeflateRect

`DeflateRect`przesunie `CRect` się, przesuwając boki w kierunku środka.

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Określa liczbę jednostek, które mają być opróżniane po lewej i prawej stronie . `CRect`

*Y*<br/>
Określa liczbę jednostek, które mają być `CRect`opróżniane na górze i na dole .

*Rozmiar*<br/>
Rozmiar [SIZE](/windows/win32/api/windef/ns-windef-size) lub [rozmiar C,](csize-class.md) który określa liczbę jednostek do opróżnienia `CRect`. Wartość `cx` określa liczbę jednostek do opróżnienia lewej i `cy` prawej strony, a wartość określa liczbę jednostek do opróżnienia górnej i dolnej części.

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` określa liczbę jednostek, które mają być opróżniane z każdej strony.

*L*<br/>
Określa liczbę jednostek, które mają być `CRect`opróżniane po lewej stronie pliku .

*t*<br/>
Określa liczbę jednostek, które mają `CRect`być opróżniane w górnej części pliku .

*R*<br/>
Określa liczbę jednostek, które mają być `CRect`opróżniane po prawej stronie pliku .

*B*<br/>
Określa liczbę jednostek, które mają `CRect`być opróżniane w dolnej części pliku .

### <a name="remarks"></a>Uwagi

Aby to `DeflateRect` zrobić, dodaje jednostki po lewej i górnej stronie i odejmuje jednostki od prawej i dolnej. Parametry są `DeflateRect` podpisane wartości; wartości dodatnie `CRect` deflate i wartości ujemne zawyżają go.

Pierwsze dwa przeciążenia opróżniają obie pary `CRect` po przeciwnych stronach, tak aby jej `cx`całkowita szerokość została zmniejszona o dwa razy *x* (lub), a jego całkowita wysokość zmniejszyła się o dwa razy *y* (lub `cy`). Pozostałe dwa przeciążenia deflate `CRect` każdej stronie niezależnie od innych.

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

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::Equalrect

Określa, `CRect` czy jest równa danego prostokąta.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt zawierający współrzędne prostokąta w lewym górnym i dolnym rogu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dwa prostokąty mają te same wartości górne, lewe, dolne i prawe; w przeciwnym razie 0.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

## <a name="crectheight"></a><a name="height"></a>CRect::Wysokość

Oblicza `CRect` wysokość, odejmując wartość górną od wartości dolnej.

```
int Height() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość `CRect`.

### <a name="remarks"></a>Uwagi

Wynikowa wartość może być ujemna.

> [!NOTE]
> Prostokąt musi zostać znormalizowany lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::InflateRect

`InflateRect`zawyża, `CRect` odsuwając boki od środka.

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Określa liczbę jednostek, które mają zawyżać lewą i prawą stronę . `CRect`

*Y*<br/>
Określa liczbę jednostek, które mają zawyżać górną i dolną część . `CRect`

*Rozmiar*<br/>
Rozmiar [SIZE](/windows/win32/api/windef/ns-windef-size) lub [rozmiar C,](csize-class.md) który określa liczbę jednostek do zawyżania `CRect`. Wartość `cx` określa liczbę jednostek do zawyżania lewej i `cy` prawej strony, a wartość określa liczbę jednostek do zawyżania górnej i dolnej części.

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` określa liczbę jednostek, które mają być zawyżane z każdej strony.

*L*<br/>
Określa liczbę jednostek, które mają zawyżać lewą stronę pliku `CRect`.

*t*<br/>
Określa liczbę jednostek, które mają `CRect`zawyżać górną część pliku .

*R*<br/>
Określa liczbę jednostek, które mają zawyżać prawą stronę pliku `CRect`.

*B*<br/>
Określa liczbę jednostek, które mają `CRect`zawyżać dno .

### <a name="remarks"></a>Uwagi

Aby to `InflateRect` zrobić, odejmuje jednostki od lewej i górnej i dodaje jednostki na prawo i dół. Parametry są `InflateRect` podpisane wartości; wartości dodatnie `CRect` zawyżają, a wartości ujemne go opróżniają.

Pierwsze dwa przeciążenia nadmuchują obie `CRect` pary po przeciwnych stronach, tak aby `cx`jej całkowita szerokość została zwiększona o dwa `cy`razy *x* (lub) i jego całkowita wysokość jest zwiększana o dwa razy *y* (lub ). Pozostałe dwa przeciążenia nadmuchują każdą stronę `CRect` niezależnie od innych.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::IntersectRect

Sprawia, `CRect` że równe przecięciu dwóch istniejących prostokątów.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt zawierający prostokąt źródłowy.

*lpRect2*<br/>
Wskazuje strukturę `RECT` `CRect` lub obiekt zawierający prostokąt źródłowy.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przecięcie nie jest puste; 0, jeśli przecięcie jest puste.

### <a name="remarks"></a>Uwagi

Przecięcie jest największym prostokątem zawartym w obu istniejących prostokątach.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::IsRectEmpty

Określa, `CRect` czy jest pusty.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CRect` jeśli jest puste; 0, `CRect` jeśli nie jest pusty.

### <a name="remarks"></a>Uwagi

Prostokąt jest pusty, jeśli szerokość i/lub wysokość są 0 lub ujemne. Różni się `IsRectNull`od , który określa, czy wszystkie współrzędne prostokąta są zerowe.

> [!NOTE]
> Prostokąt musi zostać znormalizowany lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::Isrectnull

Określa, czy górna, lewa, dolna i prawa wartość `CRect` są równe 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero `CRect`if 's top, left, bottom, i right values are all equal to 0; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Różni się `IsRectEmpty`od , który określa, czy prostokąt jest pusty.

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

## <a name="crectmovetox"></a><a name="movetox"></a>CRect::MoveToX

Wywołanie tej funkcji, aby przenieść prostokąt do bezwzględnej współrzędnej x określonej przez *x*.

```cpp
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Bezwzględna współrzędna x dla lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>CRect::MoveToXY

Wywołanie tej funkcji, aby przenieść prostokąt do bezwzględnych x- i y-współrzędne określone.

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Bezwzględna współrzędna x dla lewego górnego rogu prostokąta.

*Y*<br/>
Bezwzględna współrzędna y dla lewego górnego rogu prostokąta.

*Punkt*<br/>
Struktura `POINT` określająca bezwzględny lewy górny róg prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>CRect::MoveToY

Wywołanie tej funkcji, aby przenieść prostokąt do bezwzględnej współrzędnej y określonej przez *y*.

```cpp
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parametry

*Y*<br/>
Bezwzględna współrzędna y dla lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::NormalizeRect

Normalizuje `CRect` tak, że zarówno wysokość, jak i szerokość są dodatnie.

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>Uwagi

Prostokąt jest znormalizowany dla pozycjonowania czwartego kwadrantu, którego system Windows zwykle używa do współrzędnych. `NormalizeRect`porównuje górne i dolne wartości i zamienia je, jeśli górna część jest większa niż dolna. Podobnie zamienia wartości lewej i prawej, jeśli lewa jest większa niż po prawej stronie. Ta funkcja jest przydatna w przypadku różnych trybów mapowania i odwróconych prostokątów.

> [!NOTE]
> Następujące `CRect` funkcje prętowe wymagają znormalizowanych prostokątów, aby działały poprawnie: [Wysokość](#height), [Szerokość](#width), [Rozmiar](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [OdejmijRect](#subtractrect), [operator ==](#operator_eq_eq)operator [!=](#operator_neq), [operator &#124;](#operator_or), operator &#124;[=](#operator_or_eq), [operator &](#operator_amp)i operator [&=](#operator_amp_eq).

### <a name="example"></a>Przykład

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::OffsetRect

Przenosi `CRect` się przez określone odsunięcia.

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Określa ilość do przesuń w lewo lub w prawo. To musi być negatywne, aby przejść w lewo.

*Y*<br/>
Określa kwotę, która ma być przesuwana w górę lub w dół. To musi być negatywne, aby przejść w górę.

*Punkt*<br/>
Zawiera strukturę [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint](cpoint-class.md) określający oba wymiary, według których mają być przesuń.

*Rozmiar*<br/>
Zawiera strukturę [SIZE](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize](csize-class.md) określający oba wymiary, według których mają być przesuń.

### <a name="remarks"></a>Uwagi

Przesuwa `CRect`jednostki *x* wzdłuż osi x i *y* wzdłuż osi y. Parametry *x* i *y* są `CRect` wartościami podpisanymi, dzięki czemu można je przesuwać w lewo lub w prawo oraz w górę lub w dół.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::operator LPCRECT Konwertuje a `CRect` do [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Uwagi

Podczas korzystania z tej funkcji nie jest potrzebny**&** operator adresu ( ) . Ten operator będzie automatycznie używany podczas `CRect` przekazywania obiektu do `LPCRECT`funkcji, która oczekuje .

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::operator LPRECT

Konwertuje `CRect` a do [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Uwagi

Podczas korzystania z tej funkcji nie jest potrzebny**&** operator adresu ( ) . Ten operator będzie automatycznie używany podczas `CRect` przekazywania obiektu do `LPRECT`funkcji, która oczekuje .

### <a name="example"></a>Przykład

Zobacz przykład [CRect::operator LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::operator =

Przypisuje *srcRect* `CRect`do .

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*<br/>
Odnosi się do prostokąta źródłowego. Może to być `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) lub .

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::operator ==

Określa, `rect` czy jest `CRect` równa, porównując współrzędne ich lewego górnego i prawego dolnego rogu.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odnosi się do prostokąta źródłowego. Może to być `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) lub .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli równe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::operator !=

Określa, czy *rect* nie `CRect` jest równy, porównując współrzędne ich lewego górnego i prawego dolnego rogu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odnosi się do prostokąta źródłowego. Może to być `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) lub .

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli nie równe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::operator +=

Pierwsze dwa przeciążenia `CRect` są przesunięte przez określone przesunięcia.

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint,](cpoint-class.md) który określa liczbę jednostek do przesuń prostokąta.

*Rozmiar*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize,](csize-class.md) który określa liczbę jednostek do przesuń prostokąta.

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt zawierający liczbę jednostek, `CRect`które mają zawyżać każdą stronę programu .

### <a name="remarks"></a>Uwagi

Wartości *x* i *y* parametru `cy`(lub) `cx` `CRect`są dodawane do .

Trzecie przeciążenie `CRect` zawyża liczbę jednostek określonych w każdym człońnika parametru.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::operator -=

Pierwsze dwa przeciążenia `CRect` są przesunięte przez określone przesunięcia.

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint,](cpoint-class.md) który określa liczbę jednostek do przesuń prostokąta.

*Rozmiar*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) lub obiekt [CSize,](csize-class.md) który określa liczbę jednostek do przesuń prostokąta.

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt zawierający liczbę jednostek `CRect`do opróżnienia każdej strony programu .

### <a name="remarks"></a>Uwagi

Wartości *x* i *y* parametru `cy`(lub) `cx` są `CRect`odejmowane od .

Trzecie przeciążenie `CRect` deflates przez liczbę jednostek określonych w każdym element członkowski parametru. Należy zauważyć, że to funkcje przeciążenia, takie jak [DeflateRect](#deflaterect).

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::operator&amp;=

Ustawia `CRect` równe przecięciu `CRect` i `rect`.

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`lub .

### <a name="remarks"></a>Uwagi

Przecięcie jest największym prostokątem, który znajduje się w obu prostokątach.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

Zobacz przykład [CRect::IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::operator &#124;=

Zestawy `CRect` równe unii `CRect` i `rect`.

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera `CRect` plik RECT lub [RECT](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Uwagi

Unia jest najmniejszy prostokąt, który zawiera zarówno prostokąty źródłowe.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::operator +

Pierwsze dwa przeciążenia `CRect` zwracają obiekt, `CRect` który jest równy przesuniętemu przez określone przesunięcia.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint,](cpoint-class.md) który określa liczbę jednostek do przeniesienia wartości zwracanej.

*Rozmiar*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) lub [obiekt CSize,](csize-class.md) który określa liczbę jednostek do przeniesienia wartości zwracanej.

*Lprect*<br/>
Wskazuje na strukturę `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) lub obiekt, który zawiera liczbę jednostek do zawyżania każdej strony zwracanej wartości.

### <a name="return-value"></a>Wartość zwracana

Wynikowe z przenoszenia `CRect` `CRect` lub zawyżania przez liczbę jednostek określonych w parametrze.

### <a name="remarks"></a>Uwagi

Parametry *x* i *y parametru* `cx` `cy`(lub) `CRect`są dodawane do pozycji 's.

Trzecie przeciążenie zwraca `CRect` nowy, `CRect` który jest równy zawyżone przez liczbę jednostek określonych w każdym element członkowski parametru.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::operator -

Pierwsze dwa przeciążenia `CRect` zwracają obiekt, `CRect` który jest równy przesuniętemu przez określone przesunięcia.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Struktura [punktowa](/windows/win32/api/windef/ns-windef-point) lub `CPoint` obiekt określający liczbę jednostek do przeniesienia wartości zwracanej.

*Rozmiar*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) lub `CSize` obiekt SIZE określający liczbę jednostek do przeniesienia wartości zwracanej.

*Lprect*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt, który zawiera liczbę jednostek do opróżnienia każdej strony zwracanej wartości.

### <a name="return-value"></a>Wartość zwracana

Wynikowe z przenoszenia `CRect` `CRect` lub opróżniania przez liczbę jednostek określonych w parametrze.

### <a name="remarks"></a>Uwagi

Parametry *x* i *y* parametru (lub) `cx` `cy`są `CRect`odejmowane od pozycji 's.

Trzecie przeciążenie zwraca `CRect` nowy, `CRect` który jest równy deflated przez liczbę jednostek określonych w każdym człońnym parametru. Należy zauważyć, że to funkcje przeciążenia, takie jak [DeflateRect](#deflaterect), nie [Odejmuje.](#subtractrect)

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::operator&amp;

Zwraca `CRect` przecięcie `CRect` i *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*reect2*<br/>
Zawiera [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`lub .

### <a name="return-value"></a>Wartość zwracana

A, `CRect` który jest `CRect` przecięciem i *rect2*.

### <a name="remarks"></a>Uwagi

Przecięcie jest największym prostokątem, który znajduje się w obu prostokątach.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::operator &#124;

Zwraca `CRect` związek `CRect` i *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parametry

*reect2*<br/>
Zawiera [RECT](/windows/win32/api/windef/ns-windef-rect) `CRect`lub .

### <a name="return-value"></a>Wartość zwracana

A, `CRect` który jest `CRect` związkiem i *rect2*.

### <a name="remarks"></a>Uwagi

Unia jest najmniejszy prostokąt, który zawiera oba prostokąty.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>CRect::PtInRect

Określa, czy określony punkt `CRect`znajduje się w obrębie .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera strukturę [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint.](cpoint-class.md)

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli punkt `CRect`leży w ; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Punkt znajduje `CRect` się w środku, jeśli leży po lewej lub górnej stronie lub znajduje się we wszystkich czterech stronach. Punkt po prawej lub dolnej `CRect`stronie znajduje się na zewnątrz .

> [!NOTE]
> Prostokąt musi zostać znormalizowany lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

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

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

Ustawia wymiary `CRect` określonych współrzędnych.

```cpp
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa współrzędną x lewego górnego rogu.

*y1*<br/>
Określa współrzędną y lewego górnego rogu.

*x2*<br/>
Określa współrzędną x w prawym dolnym rogu.

*y2*<br/>
Określa współrzędną y w prawym dolnym rogu.

### <a name="example"></a>Przykład

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::SetRectEmpty

Tworzy `CRect` prostokąt zerowy, ustawiając wszystkie współrzędne na zero.

```cpp
void SetRectEmpty() throw();
```

### <a name="example"></a>Przykład

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a>CRect::ROZMIAR

I `cx` `cy` elementy członkowskie zwracanej wartości zawierają `CRect`wysokość i szerokość .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize,](csize-class.md) który zawiera `CRect`rozmiar pliku .

### <a name="remarks"></a>Uwagi

Wysokość lub szerokość mogą być ujemne.

> [!NOTE]
> Prostokąt musi zostać znormalizowany lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::OdejmowanieWyczyciek

Sprawia, że `CRect` wymiary odejmowania `lpRectSrc2` `lpRectSrc1`od .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lprectSrc1*<br/>
Wskazuje strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt, od którego ma zostać odjęty prostokąt.

*lprectSrc2*<br/>
Wskazuje strukturę `RECT` `CRect` lub obiekt, który ma zostać odjęty od prostokąta wskazywalonego przez parametr *lpRectSrc1.*

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Odejmowanie jest najmniejszym prostokątem, który zawiera wszystkie punkty w *lpRectScr1,* które nie znajdują się na przecięciu *lpRectScr1* i *lpRectScr2*.

Prostokąt określony przez *lpRectSrc1* pozostanie niezmieniony, jeśli prostokąt określony przez *lpRectSrc2* nie pokrywa się całkowicie z prostokątem określonym przez *lpRectSrc1* w co najmniej jednym z x- lub y-kierunków.

Na przykład jeśli *lpRectSrc1* były (10,10, 100,100) i *lpRectSrc2* były (50,50, 150,150), prostokąt wskazany przez *lpRectSrc1* będzie niezmieniona po powrocie funkcji. Jeśli *lpRectSrc1* były (10,10, 100,100) i *lpRectSrc2* były (50,10, 150,150), jednak prostokąt wskazany przez *lpRectSrc1* będzie zawierać współrzędne (10,10, 50,100) po powrocie funkcji.

`SubtractRect`nie jest tym samym, co [operator -](#operator_-) ani [operator -=](#operator_-_eq). Żaden z tych operatorów nigdy nie dzwoni `SubtractRect`.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

## <a name="crecttopleft"></a><a name="topleft"></a>CRect::TopLeft

Współrzędne są zwracane jako odwołanie do obiektu `CRect` [CPoint,](cpoint-class.md) który znajduje się w programie .

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Współrzędne lewego górnego rogu prostokąta.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można uzyskać lub ustawić lewy górny róg prostokąta. Ustaw narożnik, używając tej funkcji po lewej stronie operatora przypisania.

### <a name="example"></a>Przykład

Zobacz przykład [CRect::CenterPoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::UnionRect

Sprawia, że `CRect` wymiary równe unii dwóch prostokątów źródłowych.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje [rect](/windows/win32/api/windef/ns-windef-rect) lub `CRect` który zawiera prostokąt źródłowy.

*lpRect2*<br/>
Wskazuje lub `RECT` `CRect` który zawiera prostokąt źródłowy.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli unia nie jest pusta; 0, jeśli unia jest pusta.

### <a name="remarks"></a>Uwagi

Unia jest najmniejszy prostokąt, który zawiera zarówno prostokąty źródłowe.

System Windows ignoruje wymiary pustego prostokąta; oznacza to, że prostokąt, który nie ma wysokości lub nie ma szerokości.

> [!NOTE]
> Oba prostokąty muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect::Szerokość

Oblicza `CRect` szerokość, odejmując lewą wartość od prawej wartości.

```
int Width() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Szerokość . `CRect`

### <a name="remarks"></a>Uwagi

Szerokość może być ujemna.

> [!NOTE]
> Prostokąt musi zostać znormalizowany lub ta funkcja może zakończyć się niepowodzeniem. Można wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

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
[Rect](/windows/win32/api/windef/ns-windef-rect)
