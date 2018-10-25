---
title: CPoint, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2656871f62bf7881eee9c64041f3f1f492a3c948
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064891"
---
# <a name="cpoint-class"></a>CPoint, klasa

Podobnie jak Windows `POINT` struktury.

## <a name="syntax"></a>Składnia

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Konstruuje `CPoint`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::Offset](#offset)|Dodaje wartości do `x` i `y` członkowie `CPoint`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPoint::operator-](#operator_-)|Zwraca różnicę `CPoint` i rozmiarze lub negacji punktu lub różnica w rozmiarze między dwoma punktami lub przesunięcie przez ujemnym rozmiarem.|
|[CPoint::operator! =](#operator_neq)|Sprawdza, czy pod kątem nierówności pomiędzy dwoma punktami.|
|[CPoint::operator +](#operator_add)|Zwraca sumę `CPoint` i rozmiar lub punkt, czy też `CRect` przesunięty o rozmiarze.|
|[CPoint::operator +=](#operator_add_eq)|Przesuwa `CPoint` przez dodanie rozmiaru lub punktu.|
|[CPoint::operator-=](#operator_-_eq)|Przesuwa `CPoint` przez odjęcie rozmiaru lub punktu.|
|[CPoint::operator ==](#operator_eq_eq)|Sprawdza, czy pod kątem równości pomiędzy dwoma punktami.|

## <a name="remarks"></a>Uwagi

Obejmuje również funkcji elementów członkowskich do manipulowania `CPoint` i [punktu](../../mfc/reference/point-structure.md) struktury.

A `CPoint` obiekt może być używane wszędzie tam, gdzie `POINT` struktura jest używana. Operatory tej klasy, które współdziałają z "rozmiar" Zaakceptuj albo [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektów lub [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury, ponieważ są one wymienne.

> [!NOTE]
>  Ta klasa jest pochodną `tagPOINT` struktury. (Nazwa `tagPOINT` jest nazwą rzadziej używanych dla `POINT` struktury.) Oznacza to, że członkowie danych `POINT` struktury `x` i `y`, należą dane dostępne `CPoint`.

> [!NOTE]
>  Aby uzyskać więcej informacji na temat udostępnionych klasy narzędzi (takich jak `CPoint`), zobacz [udostępnionego klasy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

##  <a name="cpoint"></a>  CPoint::CPoint

Konstruuje `CPoint` obiektu.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parametry

*initX*<br/>
Określa wartość `x` członkiem `CPoint`.

*initY*<br/>
Określa wartość `y` członkiem `CPoint`.

*initPt*<br/>
[PUNKT](../../mfc/reference/point-structure.md) struktury lub `CPoint` , który określa wartości używane do zainicjowania `CPoint`.

*initSize*<br/>
[ROZMIAR](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) , który określa wartości używane do zainicjowania `CPoint`.

*dwPoint*<br/>
Zestawy `x` elementu członkowskiego na słowo mniej znaczący *dwPoint* i `y` członka do wyższego rzędu słowo *dwPoint*.

### <a name="remarks"></a>Uwagi

Jeśli nie podano argumentów, `x` i `y` elementy członkowskie są ustawione na 0.

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

##  <a name="offset"></a>  CPoint::Offset

Dodaje wartości do `x` i `y` członkowie `CPoint`.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parametry

*xOffset*<br/>
Określa ilość, o które zostanie przesunięte `x` członkiem `CPoint`.

*yOffset*<br/>
Określa ilość, o które zostanie przesunięte `y` członkiem `CPoint`.

*Punkt*<br/>
Określa ilość ( [punktu](../../mfc/reference/point-structure.md) lub `CPoint`) do przesunięcia `CPoint`.

*Rozmiar*<br/>
Określa ilość ( [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) lub [CSize](../../atl-mfc-shared/reference/csize-class.md)) do przesunięcia `CPoint`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CPoint::operator ==

Sprawdza, czy pod kątem równości pomiędzy dwoma punktami.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera [punktu](../../mfc/reference/point-structure.md) struktury lub `CPoint` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli punkty są równe; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>  CPoint::operator! =

Sprawdza, czy pod kątem nierówności pomiędzy dwoma punktami.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Zawiera [punktu](../../mfc/reference/point-structure.md) struktury lub `CPoint` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli punkty nie są równe; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CPoint::operator +=

Pierwsze przeciążenie dodaje o rozmiarze do `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.

*Punkt*<br/>
Zawiera [punktu](../../mfc/reference/point-structure.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Drugie przeciążenie dodaje wskaż `CPoint`.

W obu przypadkach dodanie odbywa się przez dodanie `x` (lub `cx`) członkiem prawostronny operand do `x` członkiem `CPoint` i dodawanie `y` (lub `cy`) członkiem prawostronny operand do `y` członkiem `CPoint`.

Na przykład dodanie `CPoint(5, -7)` do zmiennej, która zawiera `CPoint(30, 40)` zmienia zmienną `CPoint(35, 33)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CPoint::operator-=

Pierwsze przeciążenie odejmuje o rozmiarze od `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.

*Punkt*<br/>
Zawiera [punktu](../../mfc/reference/point-structure.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Drugie przeciążenie odejmuje punktu z `CPoint`.

W obu przypadkach odejmowania odbywa się przez odjęcie ilości `x` (lub `cx`) członkiem prawostronny operand z `x` członkiem `CPoint` i odejmowanie `y` (lub `cy`) po prawej stronie członka argument operacji z `y` członkiem `CPoint`.

Na przykład odjęcie `CPoint(5, -7)` ze zmiennej, która zawiera `CPoint(30, 40)` zmienia zmienną `CPoint(25, 47)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>  CPoint::operator +

Użyj tego operatora, o które zostanie przesunięte `CPoint` przez `CPoint` lub `CSize` obiektu lub przesunięcie `CRect` przez `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Zawiera [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.

*Punkt*<br/>
Zawiera [punktu](../../mfc/reference/point-structure.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.

*lprect —*<br/>
Zawiera wskaźnik do [Prostokąt](../../mfc/reference/rect-structure.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

A `CPoint` który jest przesunięty według rozmiaru, `CPoint` który jest przesunięty przez punkt, czy też `CRect` przesunięcie przez punkt.

### <a name="remarks"></a>Uwagi

Na przykład przy użyciu jednego z przeciążeń dwa pierwsze przesunięcie punktu `CPoint(25, -19)` przez punkt `CPoint(15, 5)` lub rozmiar `CSize(15, 5)` zwraca wartość `CPoint(40, -14)`.

Dodanie prostokąta do punktu zwraca prostokąt po jest przesunięty `x` i `y` wartościom określonym w punkcie. Na przykład przesunięcie prostokąt przy użyciu ostatnie przeciążenie `CRect(125, 219, 325, 419)` przez punkt `CPoint(25, -19)` zwraca `CRect(150, 200, 350, 400)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>  CPoint::operator-

Użyj jednej z dwóch pierwszych przeciążenia na potrzeby odejmowania `CPoint` lub `CSize` obiektu z `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
A [punktu](../../mfc/reference/point-structure.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.

*Rozmiar*<br/>
A [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.

*lprect —*<br/>
Wskaźnik do [Prostokąt](../../mfc/reference/rect-structure.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

A `CSize` czyli różnicę między dwoma punktami `CPoint` który jest przesunięty przez negację rozmiar `CRect` który jest przesunięty przez negację punktem lub `CPoint` czyli negacji punktu.

### <a name="remarks"></a>Uwagi

Trzecie przeciążenie przesunięcia `CRect` przez negację `CPoint`. Na koniec użyj operatora jednoargumentowego do zanegowania `CPoint`.

Na przykład użyciem pierwszego przeciążenia, aby zobaczyć różnicę między dwoma punktami `CPoint(25, -19)` i `CPoint(15, 5)` zwraca `CSize(10, -24)`.

Odejmowanie `CSize` z `CPoint` jest takie samo obliczenie opisanych powyżej, ale zwraca `CPoint` obiektu nie `CSize` obiektu. Na przykład za pomocą drugie przeciążenie, aby zobaczyć różnicę między punktem `CPoint(25, -19)` i rozmiar `CSize(15, 5)` zwraca `CPoint(10, -24)`.

Odejmowanie prostokąt z punktu zwraca przesunięcie prostokąt przy negatywów z `x` i `y` wartościom określonym w punkcie. Na przykład przesunięcie prostokąt przy użyciu ostatnie przeciążenie `CRect(125, 200, 325, 400)` przez punkt `CPoint(25, -19)` zwraca `CRect(100, 219, 300, 419)`.

Aby odwrócić punkt, należy użyć operatora jednoargumentowego. Na przykład za pomocą operatora jednoargumentowego z punktem `CPoint(25, -19)` zwraca `CPoint(-25, 19)`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbki MFC MDI](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Struktura POINT](../../mfc/reference/point-structure.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize, klasa](../../atl-mfc-shared/reference/csize-class.md)

