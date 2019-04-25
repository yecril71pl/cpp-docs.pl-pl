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
ms.openlocfilehash: 6e87d77eec526cbfcfe5c1e6e78b0287226f0613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223483"
---
# <a name="crect-class"></a>CRect, klasa

Podobnie jak Windows [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.

## <a name="syntax"></a>Składnia

```
class CRect : public tagRECT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::CRect](#crect)|Konstruuje `CRect` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Zwraca punkt prawego dolnego rogu `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Zwraca centerpoint z `CRect`.|
|[CRect::CopyRect](#copyrect)|Kopiuje wymiary prostokąta źródłowego do `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Zmniejsza szerokość i wysokość `CRect`.|
|[CRect::EqualRect](#equalrect)|Określa, czy `CRect` jest równy podanej prostokąta.|
|[CRect::Height](#height)|Oblicza wysokość `CRect`.|
|[CRect::InflateRect](#inflaterect)|Zwiększa szerokość i wysokość `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Zestawy `CRect` równą część wspólną dwóch prostokątów.|
|[CRect::IsRectEmpty](#isrectempty)|Określa, czy `CRect` jest pusty. `CRect` Jeśli szerokość lub wysokość to 0 jest pusty.|
|[CRect::IsRectNull](#isrectnull)|Określa, czy `top`, `bottom`, `left`, i `right` zmienne składowe są równe 0.|
|[CRect::MoveToX](#movetox)|Przenosi `CRect` do określonego współrzędną x.|
|[CRect::MoveToXY](#movetoxy)|Przenosi `CRect` do określonego - współrzędnych x i y.|
|[CRect::MoveToY](#movetoy)|Przenosi `CRect` do określonego współrzędną y.|
|[CRect::NormalizeRect](#normalizerect)|Standaryzuje wysokości i szerokości `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Przenosi `CRect` według określonych przesunięć.|
|[CRect::PtInRect](#ptinrect)|Określa, czy określony punkt znajduje się w obrębie `CRect`.|
|[CRect::SetRect](#setrect)|Ustawia wymiary `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Zestawy `CRect` na pusty prostokąt (wszystkie współrzędne wynosi 0).|
|[CRect::Size](#size)|Oblicza rozmiar `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Odejmuje jeden prostokąt z innego.|
|[CRect::TopLeft](#topleft)|Zwraca punkt lewym górnym rogu `CRect`.|
|[CRect::UnionRect](#unionrect)|Zestawy `CRect` równa sumę dwóch prostokątów.|
|[CRect::Width](#width)|Oblicza szerokość `CRect`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRect::operator-](#operator_-)|Odejmuje danego przesunięcia od `CRect` lub deflates `CRect` i zwraca wynikowy `CRect`.|
|[CRect::operator lpcrect —](#operator_lpcrect)|Konwertuje `CRect` do `LPCRECT`.|
|[CRect::operator lprect —](#operator_lprect)|Konwertuje `CRect` do `LPRECT`.|
|[CRect::operator! =](#operator_neq)|Określa, czy `CRect` nie jest równa prostokąta.|
|[CRect::operator &amp;](#operator_amp)|Tworzy punkt przecięcia `CRect` i prostokąt i zwraca wynikowy `CRect`.|
|[CRect::operator &amp;=](#operator_amp_eq)|Zestawy `CRect` równą część wspólną `CRect` i prostokąt.|
|[CRect::operator&#124;](#operator_or)|Tworzy złożenie `CRect` i prostokąt i zwraca wynikowy `CRect`.|
|[CRect::operator &#124;=](#operator_or_eq)|Zestawy `CRect` równa sumę `CRect` i prostokąt.|
|[CRect::operator +](#operator_add)|Dodaje dany przesunięcia do `CRect` lub zwiększa `CRect` i zwraca wynikowy `CRect`.|
|[CRect::operator +=](#operator_add_eq)|Dodaje określonego przesunięcia do `CRect` lub zwiększa `CRect`.|
|[CRect::operator =](#operator_eq)|Kopiuje wymiary prostokąta do `CRect`.|
|[CRect::operator-=](#operator_-_eq)|Odejmuje określoną przesunięcia od `CRect` lub deflates `CRect`.|
|[CRect::operator ==](#operator_eq_eq)|Określa, czy `CRect` jest taki sam, jak prostokąt.|

## <a name="remarks"></a>Uwagi

`CRect` zawiera również funkcji elementów członkowskich do manipulowania `CRect` obiektów i Windows `RECT` struktury.

A `CRect` obiekt może być przekazywany jako parametr funkcji wszędzie tam, gdzie `RECT` struktury `LPCRECT`, lub `LPRECT` mogą być przekazywane.

> [!NOTE]
> Ta klasa jest pochodną `tagRECT` struktury. (Nazwa `tagRECT` jest mniej — najczęściej używanych nazwę `RECT` struktury.) Oznacza to, że elementy członkowskie danych (`left`, `top`, `right`, i `bottom`) z `RECT` struktury są elementami członkowskimi dane dostępne `CRect`.

Element `CRect` zawiera zmienne elementu członkowskiego, które określa punkty lewym górnym rogu i prawym dolnym rogu prostokąta.

Podczas określania `CRect`, należy uważać, aby jego konstruowania, tak, aby go jest znormalizować — innymi słowy, taki sposób, że wartość lewą współrzędną jest mniejsza niż po prawej stronie u góry jest mniejsza niż dolnej. Na przykład lewym górnym rogu (10,10) i prawym dolnym rogu (20,20) definiuje znormalizowane prostokąt, ale lewym górnym rogu (20,20) i prawym dolnym rogu (10,10) definiuje nieznormalizowanego prostokąta. Jeśli prostokąt nie jest znormalizowana, wiele `CRect` funkcji elementów członkowskich może zwracać nieprawidłowe wyniki. (Zobacz [CRect::NormalizeRect](#normalizerect) listę tych funkcji.) Przed wywołaniem funkcji, która wymaga znormalizowane prostokąty można znormalizować nieznormalizowanego prostokątów przez wywołanie metody `NormalizeRect` funkcji.

Należy zachować ostrożność podczas manipulacji `CRect` z [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) i [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) funkcji elementów członkowskich. Jeśli tryb mapowania kontekstu wyświetlanie jest taka, że zakres y jest ujemna, podobnie jak w `MM_LOENGLISH`, następnie `CDC::DPtoLP` przekształci `CRect` tak, aby jego górnej jest większa od dołu. Funkcje takie jak `Height` i `Size` będą zwracać wartości ujemnych dla wysokość przekształcony `CRect`, i prostokąt będzie nieznormalizowanego.

Kiedy przy użyciu przeciążony `CRect` operatorów, pierwszy operand musi być `CRect`; drugi może być [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagRECT`

`CRect`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

##  <a name="bottomright"></a>  CRect::BottomRight

Współrzędne są zwracane jako odwołanie do [CPoint](cpoint-class.md) obiekt, który jest zawarty w `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Współrzędne prawym dolnym rogu prostokąta.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia pobieranie lub Ustawianie dolnego rogu prostokąta. Za pomocą tej funkcji po lewej stronie operatora przypisania, należy ustawić prawym górnym rogu.

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

##  <a name="centerpoint"></a>  CRect::CenterPoint

Oblicza centerpoint z `CRect` przez dodanie wartości po lewej i prawej stronie i podzielenie przez dwa i dodawanie wartości górnej i dolnej i podzielenie przez dwa.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Wartość zwracana

A `CPoint` obiekt, który jest centerpoint z `CRect`.

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

##  <a name="copyrect"></a>  CRect::CopyRect

Kopiuje `lpSrcRect` prostokąta do `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który ma zostać skopiowany.

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

##  <a name="crect"></a>  CRect::CRect

Konstruuje `CRect` obiektu.

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
Umiejscowienie lewego `CRect`.

*t*<br/>
Określa górnej części `CRect`.

*r*<br/>
Określa położenie prawo `CRect`.

*b*<br/>
Określa dolnej części `CRect`.

*srcRect*<br/>
Odwołuje się do [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) strukturę współrzędne `CRect`.

*lpSrcRect*<br/>
Wskazuje `RECT` strukturę współrzędne `CRect`.

*Punkt*<br/>
Określa punkt początku prostokąta zostać skonstruowane. Odnosi się do lewego górnego rogu.

*Rozmiar*<br/>
Określa przesunięcie w lewym górnym rogu do dolnego rogu prostokąt, można utworzyć.

*TopLeft*<br/>
Umiejscowienie lewego górnego `CRect`.

*bottomRight*<br/>
Określa położenie prawego dolnego rogu `CRect`.

### <a name="remarks"></a>Uwagi

Jeśli nie podano argumentów, `left`, `top`, `right`, i `bottom` elementy członkowskie nie są inicjowane.

`CRect`(`const RECT&`) I `CRect`(`LPCRECT`) wykonaj konstruktory [CopyRect](#copyrect). Inne konstruktory zainicjować zmienne Członkowskie obiektu bezpośrednio.

### <a name="example"></a>Przykład

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT stucture
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

##  <a name="deflaterect"></a>  CRect::DeflateRect

`DeflateRect` deflates `CRect` , przenosząc boków kierunku środka.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa liczbę jednostek do korygowania po lewej stronie i prawej krawędzi `CRect`.

*y*<br/>
Określa liczbę jednostek do korygowania górnej i dolnej części `CRect`.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) lub [CSize](csize-class.md) , który określa liczbę jednostek do korygowania `CRect`. `cx` Wartość określa liczbę jednostek do korygowania lewej i prawej stronie i `cy` wartość określa liczbę jednostek do korygowania górny i dolny.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` , który określa liczbę jednostek do korygowania każdej stronie.

*l*<br/>
Określa liczbę jednostek do korygowania po lewej stronie `CRect`.

*t*<br/>
Określa liczbę jednostek do góry korygowania `CRect`.

*r*<br/>
Określa liczbę jednostek do korygowania po prawej stronie `CRect`.

*b*<br/>
Określa liczbę jednostek do korygowania dolnej części `CRect`.

### <a name="remarks"></a>Uwagi

Aby to zrobić, `DeflateRect` dodaje jednostki do lewej i od góry i odejmuje jednostek z prawej strony i na dole. Parametry `DeflateRect` są podpisane wartości; wartości dodatnich deflate `CRect` i wartości ujemnych rozszerzanie go.

Pierwsze dwa przeciążenia deflate pary przeciwny stron `CRect` tak, aby jego łączna szerokość zmniejszyła się przez dwa razy *x* (lub `cx`) i jego całkowita wysokość zmniejszyła się przez dwa razy *y* () lub `cy`). Dwa przeciążenia deflate po obu stronach `CRect` niezależnie od innych.

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

##  <a name="equalrect"></a>  CRect::EqualRect

Określa, czy `CRect` jest równy podanej prostokąta.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera współrzędne górnego lewego i prawego dolnego rogu prostokąta.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dwa prostokąty mają tego samego początku, po lewej stronie, dolnej i odpowiednie wartości. w przeciwnym razie 0.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

##  <a name="height"></a>  CRect::Height

Oblicza wysokość `CRect` przez odjęcie najwyższą wartość z wartości dolnej.

```
int Height() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość `CRect`.

### <a name="remarks"></a>Uwagi

Wartość wynikowa może być ujemna.

> [!NOTE]
>  Prostokąt muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect` zwiększa `CRect` , przenosząc boków od jej środka.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa liczbę jednostek można zwiększyć po lewej stronie i prawej krawędzi `CRect`.

*y*<br/>
Określa liczbę jednostek rozszerzanie górnej i dolnej części `CRect`.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) lub [CSize](csize-class.md) , który określa liczbę jednostek rozszerzanie `CRect`. `cx` Wartość określa liczbę jednostek rozszerzanie lewej i prawej stronie i `cy` wartość określa liczbę jednostek, aby zwiększyć górny i dolny.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` , który określa liczbę jednostek po każdej stronie Rozszerzanie.

*l*<br/>
Określa liczbę jednostek po lewej stronie Rozszerzanie `CRect`.

*t*<br/>
Określa liczbę jednostek do góry rozszerzanie `CRect`.

*r*<br/>
Określa liczbę jednostek po prawej stronie Rozszerzanie `CRect`.

*b*<br/>
Określa liczbę jednostek do dolnej części Rozszerzanie `CRect`.

### <a name="remarks"></a>Uwagi

Aby to zrobić, `InflateRect` odejmuje jednostek z lewej strony i od góry i dodaje jednostek w prawo i w dół. Parametry `InflateRect` są podpisane wartości dodatnie wartości rozszerzanie `CRect` i wartości ujemnych deflate go.

Pierwsze dwa przeciążenia rozszerzanie pary przeciwny stron `CRect` tak, aby jego łączna szerokość zwiększa się o dwa razy *x* (lub `cx`) i jego całkowita wysokość zwiększa się o dwa razy *y* () lub `cy`). Dwa przeciążenia rozszerzanie po obu stronach `CRect` niezależnie od innych.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

Sprawia, że `CRect` równą część wspólną dwóch istniejących prostokątów.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera prostokąta źródłowego.

*lpRect2*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera prostokąta źródłowego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli część wspólną nie jest pusta. 0, jeśli część wspólną jest pusty.

### <a name="remarks"></a>Uwagi

Przecięcie jest największy prostokąt, które są zawarte w obu istniejących prostokąty.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rectOne(125, 0, 150, 200);
CRect rectTwo(0, 75, 350,  95);
CRect rectInter;
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

##  <a name="isrectempty"></a>  CRect::IsRectEmpty

Określa, czy `CRect` jest pusty.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CRect` jest pusty, a 0 Jeśli `CRect` nie jest pusty.

### <a name="remarks"></a>Uwagi

Prostokąt jest pusta, jeśli szerokość lub wysokość 0 lub ujemna. Różni się od `IsRectNull`, która określa, czy wszystkie współrzędnych prostokąta to zero.

> [!NOTE]
>  Prostokąt muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
```cpp
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>  CRect::IsRectNull

Określa, czy lewym górnym rogu, bottom i kliknij prawym przyciskiem myszy wartości `CRect` są równe 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CRect`w lewym górnym rogu, dół, a odpowiednie wartości są wszystkie równa 0, a w przeciwnym 0.

### <a name="remarks"></a>Uwagi

Różni się od `IsRectEmpty`, która określa, czy prostokąta jest pusty.

### <a name="example"></a>Przykład

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
```cpp
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>  CRect::MoveToX

Wywołaj tę funkcję, aby przenieść prostokąt bezwzględne współrzędną x określone przez *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Bezwzględny współrzędną x do lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);
```cpp
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

Wywołaj tę funkcję można przesuwać do bezwzględnych współrzędnych x i y-określony.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Bezwzględny współrzędną x do lewego górnego rogu prostokąta.

*y*<br/>
Bezwzględny współrzędną y lewego górnego rogu prostokąta.

*Punkt*<br/>
A `POINT` struktury, określając bezwzględne lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
```cpp
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>  CRect::MoveToY

Wywołaj tę funkcję, aby przenieść prostokąt bezwzględne współrzędną y punktu określonego przez *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parametry

*y*<br/>
Bezwzględny współrzędną y lewego górnego rogu prostokąta.

### <a name="example"></a>Przykład

```cpp
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
   // rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>  CRect::NormalizeRect

Normalizuje `CRect` tak, aby wysokość i szerokość są dodatnie.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Uwagi

Prostokąt jest znormalizować do czwartej quadrant pozycjonowania, przypadków, której Windows używa się zazwyczaj dla współrzędnych. `NormalizeRect` porównuje wartości górnej i dolnej i zamienia je, jeśli u góry jest większa od dołu. Podobnie jego zamienia wartości po lewej i prawej stronie, jeśli po lewej stronie jest większa niż po prawej stronie. Ta funkcja jest przydatne podczas rozwiązywania problemów związanych z trybami innego mapowania i odwrócony prostokąty.

> [!NOTE]
> Następujące `CRect` funkcji elementów członkowskich wymagają znormalizowane prostokątów, aby zapewnić prawidłowe działanie: [Wysokość](#height), [szerokość](#width), [rozmiar](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operator ==](#operator_eq_eq), [operator! =](#operator_neq), [operator &#124; ](#operator_or), [operator &#124;=](#operator_or_eq), [operator &](#operator_amp), i [operator & =](#operator_amp_eq).

### <a name="example"></a>Przykład

```cpp
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
   rect1.NormalizeRect();
   rect2.NormalizeRect();
   ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

Przenosi `CRect` według określonych przesunięć.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa, aby przesunąć w lewo lub w prawo. Musi być ujemna na Przenieś w lewo.

*y*<br/>
Określa, jak przenieść w górę lub w dół. Musi być ujemna na Przenieś w górę.

*Punkt*<br/>
Zawiera [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub [CPoint](cpoint-class.md) określający oba wymiary, według którego ma zostać przeniesiona.

*Rozmiar*<br/>
Zawiera [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub [CSize](csize-class.md) określający oba wymiary, według którego ma zostać przeniesiona.

### <a name="remarks"></a>Uwagi

Przenosi `CRect` *x* jednostek wzdłuż osi x i *y* jednostki wzdłuż osi y. *x* i *y* parametry są wartościami podpisem, więc `CRect` mogą zostać przeniesione w lewo lub w prawo i w górę lub w dół.

### <a name="example"></a>Przykład

```cpp
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>  Konwertuje lpcrect — CRect::operator `CRect` do [lpcrect —](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Uwagi

Podczas korzystania z tej funkcji nie ma potrzeby address-of (**&**) — operator. Ten operator będzie automatycznie używane podczas przekazywania `CRect` obiektu do funkcji, która oczekuje `LPCRECT`.

##  <a name="operator_lprect"></a>  CRect::operator lprect —

Konwertuje `CRect` do [lprect —](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Uwagi

Podczas korzystania z tej funkcji nie ma potrzeby address-of (**&**) — operator. Ten operator będzie automatycznie używane podczas przekazywania `CRect` obiektu do funkcji, która oczekuje `LPRECT`.

### <a name="example"></a>Przykład

Zobacz przykład [lpcrect — CRect::operator](#operator_lpcrect).

##  <a name="operator_eq"></a>  CRect::operator =

Przypisuje *srcRect* do `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parametry

*srcRect*<br/>
Odnosi się do prostokąta źródłowego. Może być [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="example"></a>Przykład

```cpp
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>  CRect::operator ==

Określa, czy `rect` jest równa `CRect` porównując współrzędne rogach lewym górnym i dolnym rogu.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odnosi się do prostokąta źródłowego. Może być [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli są równe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

##  <a name="operator_neq"></a>  CRect::operator! =

Określa, czy *prostokąt* nie jest równa `CRect` porównując współrzędne rogach lewym górnym i dolnym rogu.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odnosi się do prostokąta źródłowego. Może być [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli nie jest równe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

##  <a name="operator_add_eq"></a>  CRect::operator +=

Pierwsze dwa przeciążenia przenieść `CRect` według określonych przesunięć.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
A [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek można przenieść prostokąt.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek można przenieść prostokąt.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera liczbę jednostek po każdej stronie Rozszerzanie `CRect`.

### <a name="remarks"></a>Uwagi

Parametr *x* i *y* (lub `cx` i `cy`) wartości są dodawane do `CRect`.

Trzecie przeciążenie zwiększa `CRect` , liczba jednostek określona w każdym elemencie członkowskim parametru.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint  pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>  CRect::operator-=

Pierwsze dwa przeciążenia przenieść `CRect` według określonych przesunięć.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
A [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek można przenieść prostokąt.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek można przenieść prostokąt.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera liczbę jednostek do korygowania każdej strony `CRect`.

### <a name="remarks"></a>Uwagi

Parametr *x* i *y* (lub `cx` i `cy`) wartości są odejmowane od `CRect`.

Trzecie przeciążenie deflates `CRect` , liczba jednostek określona w każdym elemencie członkowskim parametru. Należy zauważyć, że tego przeciążenia funkcji, takich jak [DeflateRect](#deflaterect).

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>  CRect::operator &amp;=

Zestawy `CRect` równą część wspólną `CRect` i `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="remarks"></a>Uwagi

Przecięcie jest największy prostokąt, który znajduje się w obu prostokąty.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

Zobacz przykład [CRect::IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>  CRect::operator &#124;=

Zestawy `CRect` równa sumę `CRect` i `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera `CRect` lub [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect).

### <a name="remarks"></a>Uwagi

Unia jest najmniejsza prostokąt, który zawiera oba prostokąty źródła.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>  CRect::operator +

Zwraca pierwsze dwa przeciążenia `CRect` obiektu, który jest równy `CRect` przesunięty przez określonych przesunięć.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
A [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek można przenieść wartość zwracaną.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek można przenieść wartość zwracaną.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera liczbę jednostek rozszerzanie na każdej stronie zwracanej wartości.

### <a name="return-value"></a>Wartość zwracana

`CRect` Wyniku przenoszenia lub pompowania `CRect` według liczby jednostek określonego w parametrze.

### <a name="remarks"></a>Uwagi

Parametr *x* i *y* (lub `cx` i `cy`) parametry są dodawane do `CRect`jego położenie.

Trzecie przeciążenie zwraca nowy `CRect` jest równa `CRect` zwiększony, liczba jednostek określona w każdym elemencie członkowskim parametru.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>  CRect::operator-

Zwraca pierwsze dwa przeciążenia `CRect` obiektu, który jest równy `CRect` przesunięty przez określonych przesunięć.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
A [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub `CPoint` obiekt, który określa liczbę jednostek można przenieść wartość zwracaną.

*Rozmiar*<br/>
A [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub `CSize` obiekt, który określa liczbę jednostek można przenieść wartość zwracaną.

*lpRect*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiekt, który zawiera liczbę jednostek do korygowania każdej stronie zwracanej wartości.

### <a name="return-value"></a>Wartość zwracana

`CRect` Wyniku przenoszenia lub przeliczania `CRect` według liczby jednostek określonego w parametrze.

### <a name="remarks"></a>Uwagi

Parametr *x* i *y* (lub `cx` i `cy`) parametry są odejmowane od `CRect`jego położenie.

Trzecie przeciążenie zwraca nowy `CRect` jest równa `CRect` zmniejszony, liczba jednostek określona w każdym elemencie członkowskim parametru. Należy zauważyć, że tego przeciążenia funkcji, takich jak [DeflateRect](#deflaterect), a nie [SubtractRect](#subtractrect).

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>  CRect::operator &amp;

Zwraca `CRect` oznacza to część wspólną `CRect` i *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Zawiera [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="return-value"></a>Wartość zwracana

A `CRect` oznacza to część wspólną `CRect` i *rect2*.

### <a name="remarks"></a>Uwagi

Przecięcie jest największy prostokąt, który znajduje się w obu prostokąty.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>  CRect::operator&#124;

Zwraca `CRect` to znaczy sumę `CRect` i *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parametry

*rect2*<br/>
Zawiera [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect`.

### <a name="return-value"></a>Wartość zwracana

A `CRect` to znaczy sumę `CRect` i *rect2*.

### <a name="remarks"></a>Uwagi

Unia jest najmniejsza prostokąt, który zawiera oba prostokąty.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>  CRect::PtInRect

Określa, czy określony punkt znajduje się w obrębie `CRect`.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera [punktu](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub [CPoint](cpoint-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli punkt znajduje się w obrębie `CRect`; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Punkt znajduje się w `CRect` jeśli leży po stronie lewej lub górnej lub jest w ramach wszystkich czterech stron. Punkt po prawej stronie lub u dołu strony znajduje się poza `CRect`.

> [!NOTE]
>  Prostokąt muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

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

##  <a name="setrect"></a>  CRect::SetRect

Ustawia wymiary `CRect` do określonych współrzędnych.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa współrzędną x lewego górnego rogu.

*y1*<br/>
Określa współrzędną y lewego górnego rogu.

*x2*<br/>
Określa współrzędną x prawym dolnym rogu.

*y2*<br/>
Określa współrzędną y prawego dolnego rogu.

### <a name="example"></a>Przykład

```cpp
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>  CRect::SetRectEmpty

Sprawia, że `CRect` prostokąt o wartości null, ustawiając wszystkie współrzędne na zero.

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

##  <a name="size"></a>  CRect::SIZE

`cx` i `cy` członkowie wartość zwracana zawiera wysokości i szerokości `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Wartość zwracana

A [CSize](csize-class.md) obiekt, który zawiera rozmiar `CRect`.

### <a name="remarks"></a>Uwagi

Wysokość i szerokość może być ujemna.

> [!NOTE]
>  Prostokąt muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

Sprawia, że wymiary `CRect` równa odejmowania `lpRectSrc2` z `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parametry

*lpRectSrc1*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury lub `CRect` obiektu, z którego ma być odjęta prostokąta.

*lpRectSrc2*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który jest odjęta od prostokąta wskazywany przez *lpRectSrc1* parametru.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Odejmowania jest najmniejsza prostokąt, który zawiera wszystkie punkty w *lpRectScr1* nie znajdują się w część wspólną *lpRectScr1* i *lpRectScr2*.

Prostokąt określony przez *lpRectSrc1* pozostaje bez zmian, jeśli prostokąt określony przez *lpRectSrc2* całkowicie nie pokrywa się prostokąt określony przez *lpRectSrc1*w co najmniej jednym z x - lub y instrukcjami.

Na przykład jeśli *lpRectSrc1* zostały (10,10, 100,100) i *lpRectSrc2* zostały (50,50, 150,150) prostokąta wskazywany przez *lpRectSrc1* będzie pozostanie niezmieniona po zwrócona przez funkcję. Jeśli *lpRectSrc1* zostały (10,10, 100,100) i *lpRectSrc2* zostały (50,10, 150,150), jednak prostokąta wskazywany przez *lpRectSrc1* będzie zawierać współrzędne (10,10, 50,100), gdy wartość zwrócona przez funkcję.

`SubtractRect` nie jest taka sama jak [operator -](#operator_-) ani [operator-=](#operator_-_eq). Żadna z tych operatorów nigdy nie wywołuje `SubtractRect`.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

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

##  <a name="topleft"></a>  CRect::TopLeft

Współrzędne są zwracane jako odwołanie do [CPoint](cpoint-class.md) obiekt, który jest zawarty w `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Współrzędne lewego górnego rogu prostokąta.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia albo Pobierz lub ustaw lewego górnego rogu prostokąta. Za pomocą tej funkcji po lewej stronie operatora przypisania, należy ustawić prawym górnym rogu.

### <a name="example"></a>Przykład

Zobacz przykład [CRect::CenterPoint](#centerpoint).

##  <a name="unionrect"></a>  CRect::UnionRect

Sprawia, że wymiary `CRect` równa Unii prostokąty dwa źródła.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parametry

*lpRect1*<br/>
Wskazuje [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect` zawierający prostokąta źródłowego.

*lpRect2*<br/>
Wskazuje `RECT` lub `CRect` zawierający prostokąta źródłowego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeżeli Unia nie jest puste. 0, jeśli Unii jest pusty.

### <a name="remarks"></a>Uwagi

Unia jest najmniejsza prostokąt, który zawiera oba prostokąty źródła.

Windows ignoruje wymiary prostokąta pusty; oznacza to, że prostokąt, który ma wysokość lub szerokość nie ma.

> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);
```

##  <a name="width"></a>  CRect::Width

Oblicza szerokość `CRect` przez odjęcie wartości po lewej stronie od prawej wartości.

```
int Width() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Szerokość `CRect`.

### <a name="remarks"></a>Uwagi

Szerokość może być ujemna.

> [!NOTE]
>  Prostokąt muszą być znormalizowane lub ta funkcja może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąta przed wywołaniem tej funkcji.

### <a name="example"></a>Przykład

```cpp
   CRect rect(20, 30, 80, 70);
   int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);
```

## <a name="see-also"></a>Zobacz także

[CPoint, klasa](cpoint-class.md)<br/>
[CSize, klasa](csize-class.md)<br/>
[RECT](/windows/desktop/api/windef/ns-windef-tagrect)
