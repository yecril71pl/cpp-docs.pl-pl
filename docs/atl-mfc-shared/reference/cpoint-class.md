---
title: CPoint, klasa
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: a806cfa18119df9beef3e070a65bc238a12580a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317721"
---
# <a name="cpoint-class"></a>CPoint, klasa

Podobnie jak `POINT` w strukturze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Konstruuje `CPoint`plik .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::Przesunięcie](#offset)|Dodaje wartości `x` do `y` i `CPoint`członków .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::operator -](#operator_-)|Zwraca różnicę a `CPoint` i rozmiar lub negację punktu lub różnicę wielkości między dwoma punktami lub przesunięcie o rozmiar ujemny.|
|[CPoint::operator !=](#operator_neq)|Sprawdza nierówność między dwoma punktami.|
|[CPoint::operator +](#operator_add)|Zwraca sumę `CPoint` rozmiaru lub punktu lub `CRect` odsunięcia o rozmiar.|
|[CPoint::operator +=](#operator_add_eq)|Odsunięcia `CPoint` przez dodanie rozmiaru lub punktu.|
|[CPoint::operator -=](#operator_-_eq)|Odsunięcia `CPoint` przez odjęcie rozmiaru lub punktu.|
|[CPoint::operator ==](#operator_eq_eq)|Sprawdza równość między dwoma punktami.|

## <a name="remarks"></a>Uwagi

Zawiera również funkcje elementów członkowskich do manipulowania `CPoint` i [point](/windows/win32/api/windef/ns-windef-point) struktur.

Obiekt `CPoint` może być używany `POINT` wszędzie tam, gdzie używana jest struktura. Operatory tej klasy, które współdziałają z "size" zaakceptować [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektów lub [size](/windows/win32/api/windef/ns-windef-size) struktur, ponieważ dwa są wymienne.

> [!NOTE]
> Ta klasa jest pochodną `tagPOINT` struktury. (Nazwa `tagPOINT` jest rzadziej używaną nazwą `POINT` struktury). `POINT` Oznacza to, `x` że elementy członkowskie `y`danych struktury i `CPoint`, są dostępne elementy członkowskie danych .

> [!NOTE]
> Aby uzyskać więcej informacji na `CPoint`temat udostępnionych klas narzędziowych (np. [Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint::CPoint

Konstruuje `CPoint` obiekt.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parametry

*initX*<br/>
Określa wartość `x` elementu członkowskiego `CPoint`.

*initY*<br/>
Określa wartość `y` elementu członkowskiego `CPoint`.

*initpt (initpt)*<br/>
[point](/windows/win32/api/windef/ns-windef-point) lub `CPoint` określający wartości używane do `CPoint`inicjowania .

*initSize (rozmiar)*<br/>
[Struktura SIZE](/windows/win32/api/windef/ns-windef-size) lub [CSize](../../atl-mfc-shared/reference/csize-class.md) określająca wartości `CPoint`używane do inicjowania .

*dwPoint (punkt z punktu widzenia dw*<br/>
Ustawia `x` członka na słowo niskiej kolejności *dwPoint* i `y` członka do wysokiej kolejności słowo *dwPoint*.

### <a name="remarks"></a>Uwagi

Jeśli nie podano `x` żadnych `y` argumentów, a członkowie są ustawione na 0.

### <a name="example"></a>Przykład

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

## <a name="cpointoffset"></a><a name="offset"></a>CPoint::Przesunięcie

Dodaje wartości `x` do `y` i `CPoint`członków .

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*xOffset (Zestawoffset)*<br/>
Określa kwotę do `x` przesunięcia `CPoint`elementu członkowskiego .

*yOffset (zestaw)*<br/>
Określa kwotę do `y` przesunięcia `CPoint`elementu członkowskiego .

*Punkt*<br/>
Określa kwotę ( [POINT](/windows/win32/api/windef/ns-windef-point) PUNKT `CPoint`lub ) `CPoint`do przesunięcia .

*Rozmiar*<br/>
Określa kwotę [(SIZE](/windows/win32/api/windef/ns-windef-size) lub [CSize),](../../atl-mfc-shared/reference/csize-class.md) `CPoint`aby zrównoważyć .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::operator ==

Sprawdza równość między dwoma punktami.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera strukturę `CPoint` lub obiekt [POINT.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli punkty są równe; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::operator !=

Sprawdza nierówność między dwoma punktami.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera strukturę `CPoint` lub obiekt [POINT.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli punkty nie są równe; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::operator +=

Pierwsze przeciążenie dodaje rozmiar `CPoint`do .

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera strukturę [SIZE](/windows/win32/api/windef/ns-windef-size) lub [obiekt CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Zawiera strukturę [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Uwagi

Drugie przeciążenie dodaje punkt `CPoint`do .

W obu przypadkach dodawanie odbywa `x` się `cx`przez dodanie (lub) członka prawej `x` opery `CPoint` do `y` członka `cy`członka (lub) członka prawej opery `y` do `CPoint`członka .

Na przykład `CPoint(5, -7)` dodanie do zmiennej, która zawiera `CPoint(30, 40)` zmienia zmienną na `CPoint(35, 33)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::operator -=

Pierwsze przeciążenie odejmuje `CPoint`rozmiar od pliku .

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera strukturę [SIZE](/windows/win32/api/windef/ns-windef-size) lub [obiekt CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Zawiera strukturę [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Uwagi

Drugie przeciążenie odejmuje `CPoint`punkt od pliku .

W obu przypadkach odejmowanie odbywa się `x` poprzez `cx`odjęcie (lub) członka `x` prawej `CPoint` opery od `y` członka `cy`członka (lub) członka prawej opery `y` od `CPoint`członka .

Na przykład odejmianie `CPoint(5, -7)` od `CPoint(30, 40)` zmiennej, `CPoint(25, 47)`która zawiera zmienia zmienną na .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::operator +

Ten operator służy `CPoint` do `CPoint` `CSize` równu przez lub `CRect` obiektu, lub do odsunięcia a przez `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera strukturę [SIZE](/windows/win32/api/windef/ns-windef-size) lub [obiekt CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Zawiera strukturę [POINT](/windows/win32/api/windef/ns-windef-point) lub obiekt [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

*Lprect*<br/>
Zawiera wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

A, `CPoint` który jest przesunięty przez rozmiar, `CPoint` który `CRect` jest odsunięty przez punkt lub odsunięte przez punkt.

### <a name="remarks"></a>Uwagi

Na przykład użycie jednego z pierwszych dwóch przeciążeń w celu przesunięcia `CPoint(25, -19)` punktu o punkt `CPoint(15, 5)` lub rozmiar `CSize(15, 5)` zwraca wartość `CPoint(40, -14)`.

Dodanie prostokąta do punktu zwraca prostokąt po odsunięciu przez `x` wartości i `y` wartości określone w punkcie. Na przykład za pomocą ostatniego przeciążenia, aby `CPoint(25, -19)` `CRect(150, 200, 350, 400)`odsunąć prostokąt `CRect(125, 219, 325, 419)` o punkt zwraca .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::operator -

Użyj jednego z dwóch pierwszych przeciążeń, `CPoint` `CSize` aby `CPoint`odjąć obiekt lub obiekt od pliku .

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) lub [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

*Rozmiar*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) lub [obiekt CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Lprect*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

A, `CSize` która jest różnica między `CPoint` dwoma punktami, a, który `CRect` jest przesunięty przez negację rozmiaru, a, który jest przesunięty przez negację punktu `CPoint` lub, który jest negacją punktu.

### <a name="remarks"></a>Uwagi

Trzecie przeciążenie przesunie `CRect` a `CPoint`przez negację . Na koniec użyj operatora unary, `CPoint`aby zanegować .

Na przykład za pomocą pierwszego przeciążenia, `CPoint(25, -19)` aby `CPoint(15, 5)` `CSize(10, -24)`znaleźć różnicę między dwoma punktami i zwraca .

Odejmowanie `CSize` `CPoint` od wykonuje te same obliczenia `CPoint` co powyżej, ale zwraca obiekt, a `CSize` nie obiekt. Na przykład za pomocą drugiego przeciążenia, `CPoint(25, -19)` aby znaleźć `CSize(15, 5)` `CPoint(10, -24)`różnicę między punktem a rozmiar zwraca .

Odejmowanie prostokąta od punktu zwraca prostokąt odsunięty przez `x` `y` negatywy i wartości określone w punkcie. Na przykład za pomocą ostatniego przeciążenia, aby `CPoint(25, -19)` `CRect(100, 219, 300, 419)`odsunąć prostokąt `CRect(125, 200, 325, 400)` przez punkt zwraca .

Operator unary służy do negowania punktu. Na przykład przy użyciu operatora unary z punktem `CPoint(25, -19)` zwraca `CPoint(-25, 19)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Struktura POINT](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize, klasa](../../atl-mfc-shared/reference/csize-class.md)
