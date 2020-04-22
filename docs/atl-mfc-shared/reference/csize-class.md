---
title: CSize, klasa
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: dc876781cca568a332072938bec2cda0afb2ac8b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746971"
---
# <a name="csize-class"></a>CSize, klasa

Podobnie jak [w](/windows/win32/api/windef/ns-windef-size) strukturze Rozmiar systemu Windows, która implementuje względną współrzędną lub położenie.

## <a name="syntax"></a>Składnia

```
class CSize : public tagSIZE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Rozmiar CSize::Rozmiar CSize](#csize)|Konstruuje `CSize` obiekt.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSize::operator -](#operator_-)|Odejmuje dwa rozmiary.|
|[CSize::operator !=](#operator_neq)|Sprawdza, czy `CSize` nie ma nierówności między rozmiarem i ich rozmiarem.|
|[Rozmiar C::operator +](#operator_add)|Dodaje dwa rozmiary.|
|[CSize::operator +=](#operator_add_eq)|Dodaje rozmiar `CSize`do pliku .|
|[Rozmiar C::operator -=](#operator_-_eq)|Odejmuje rozmiar `CSize`od pliku .|
|[Rozmiar C::operator ==](#operator_eq_eq)|Sprawdza, czy `CSize` między równością i rozmiarem.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną `SIZE` struktury. Oznacza to, że `CSize` można przekazać w `SIZE` parametr, który wymaga `SIZE` a i że `CSize`elementy członkowskie danych struktury są dostępne elementy członkowskie danych .

I `cx` `cy` członkowie `SIZE` (i) `CSize`są publiczne. Ponadto `CSize` implementuje funkcje członkowskie do `SIZE` manipulowania strukturą.

> [!NOTE]
> Aby uzyskać więcej informacji na `CSize`temat udostępnionych klas narzędziowych (np. [Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

## <a name="csizecsize"></a><a name="csize"></a>Rozmiar CSize::Rozmiar CSize

Konstruuje `CSize` obiekt.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parametry

*initCX*<br/>
Ustawia `cx` element członkowski `CSize`dla .

*initCY*<br/>
Ustawia `cy` element członkowski `CSize`dla .

*initSize (rozmiar)*<br/>
[Struktura](/windows/win32/api/windef/ns-windef-size) rozmiar `CSize` lub obiekt `CSize`używany do inicjowania .

*initpt (initpt)*<br/>
[Struktura](/windows/win32/api/windef/ns-windef-point) POINT `CPoint` lub obiekt `CSize`używany do inicjowania .

*dwSize (rozmiar)*<br/>
DWORD używany do `CSize`inicjowania . Słowo niskiego rzędu `cx` jest elementem członkowskim, a `cy` wyraz wysokiego rzędu jest członkiem.

### <a name="remarks"></a>Uwagi

Jeśli nie podano `cx` żadnych `cy` argumentów i są inicjowane do zera.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>Rozmiar C::operator ==

Sprawdza równość między dwoma rozmiarami.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość niezerowa, jeśli rozmiary są równe, otherwize 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::operator !=

Sprawdza nierówność między dwoma rozmiarami.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość niezerowa, jeśli rozmiary nie są równe, w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>CSize::operator +=

Dodaje rozmiar do `CSize`tego .

```cpp
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>Rozmiar C::operator -=

Odejmuje rozmiar `CSize`od tego .

```cpp
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>Rozmiar C::operator +

Te operatory `CSize` dodać tę wartość do wartości parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Uwagi

Zobacz następujące opisy poszczególnych operatorów:

- **operator +(** *rozmiar* **)**

  Ta operacja `CSize` dodaje dwie wartości.

- **operator +(** *punkt* **)**

  Ta operacja odsuwa (przenosi) wartość [POINT](/windows/win32/api/windef/ns-windef-point) `CSize` (lub [CPoint)](../../atl-mfc-shared/reference/cpoint-class.md)o tę wartość. I `cx` `cy` członków tej `CSize` wartości są `x` dodawane do `y` `POINT` i danych członków wartości. Jest analogiczna do wersji [CPoint::operator +,](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) która przyjmuje parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operator +(** *lpRect* **)**

   Ta operacja odsuwa (przenosi) wartość [RECT](/windows/win32/api/windef/ns-windef-rect) (lub [CRect)](../../atl-mfc-shared/reference/crect-class.md)o tę `CSize` wartość. Elementy `cx` `cy` członkowskie tej `CSize` wartości są `left`dodawane `right`do `bottom` , `top`, `RECT` i elementy członkowskie danych wartości. Jest analogiczna do wersji [CRect::operator +,](../../atl-mfc-shared/reference/crect-class.md#operator_add) która przyjmuje parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize::operator -

Pierwsze trzy z tych operatorów `CSize` odjąć tę wartość do wartości parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Czwarty operator, unary minus, zmienia znak `CSize` wartości. Zobacz następujące opisy poszczególnych operatorów:

- **operator -(** *rozmiar* **)**

  Ta operacja odejmuje dwie `CSize` wartości.

- **operator -(** *punkt* **)**

  Ta operacja odsuwa (przenosi) wartość [POINT](/windows/win32/api/windef/ns-windef-point) lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) przez odwrotność dodatku tej `CSize` wartości. I `cx` `cy` tej `CSize` wartości są odejmowane od `x` i `POINT` `y` danych elementów członkowskich wartości. Jest analogiczna do wersji [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) która przyjmuje parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operator -(** *lpRect* **)**

  Ta operacja odsuwa (przenosi) wartość [RECT](/windows/win32/api/windef/ns-windef-rect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) przez odwrotność dodatku tej `CSize` wartości. Elementy `cx` `cy` członkowskie tej `CSize` wartości są odejmowane `right`od `bottom` `left` `top`, , `RECT` i elementy członkowskie danych wartości. Jest analogiczna do wersji [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) która przyjmuje parametr [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operator -()**

  Ta operacja zwraca odwrotność `CSize` dodatku tej wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint, klasa](../../atl-mfc-shared/reference/cpoint-class.md)
