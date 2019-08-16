---
title: Klasa CSize
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
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491653"
---
# <a name="csize-class"></a>Klasa CSize

Podobnie jak w przypadku struktury [rozmiaru](/windows/win32/api/windef/ns-windef-size) systemu Windows, która implementuje względną współrzędną lub położeniu.

## <a name="syntax"></a>Składnia

```
class CSize : public tagSIZE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSize:: CSize](#csize)|Konstruuje `CSize` obiekt.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSize:: operator-](#operator_-)|Odejmuje dwa rozmiary.|
|[CSize:: operator! =](#operator_neq)|Sprawdza pod kątem nierówności między `CSize` i rozmiarem.|
|[CSize:: operator +](#operator_add)|Dodaje dwa rozmiary.|
|[CSize:: operator + =](#operator_add_eq)|Dodaje rozmiar do `CSize`.|
|[CSize:: operator-=](#operator_-_eq)|Odejmuje rozmiar od `CSize`.|
|[CSize:: operator = =](#operator_eq_eq)|Sprawdza równość między `CSize` i rozmiarem.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną `SIZE` struktury. Oznacza to, że można przekazać `CSize` do parametru, który wywołuje `SIZE` dla a i że elementy członkowskie `SIZE` danych struktury są dostępnymi elementami członkowskimi `CSize`danych.

Elementy `cx` `cy` isąpubliczne`CSize`. `SIZE` Ponadto `CSize` implementuje funkcje elementów członkowskich do `SIZE` manipulowania strukturą.

> [!NOTE]
> Aby uzyskać więcej informacji na temat udostępnionych klas narzędzi `CSize`(takich jak), zobacz [klasy udostępnione](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes. h

##  <a name="csize"></a>CSize:: CSize

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
Ustawia element członkowski dla elementu `CSize`. `cx`

*initCY*<br/>
Ustawia element członkowski dla elementu `CSize`. `cy`

*initSize*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) lub `CSize` obiekt używany do inicjowania `CSize`.

*initPt*<br/>
Struktura [punktu](/windows/win32/api/windef/ns-windef-point) lub `CPoint` obiekt używany do inicjowania `CSize`.

*dwSize*<br/>
Wartość DWORD użyta `CSize`do zainicjowania. Słowo o niskim porządku to `cx` element członkowski, a `cy` jest to element członkowski o wysokim poziomie kolejności.

### <a name="remarks"></a>Uwagi

Jeśli nie podano `cx` argumentów i `cy` są one inicjowane na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize:: operator = =

Sprawdza równość między dwoma rozmiarami.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość różną od zera, jeśli rozmiary są równe, otherwize 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize:: operator! =

Sprawdza nierówność między dwoma rozmiarami.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość różną od zera, jeśli rozmiary nie są równe. w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize:: operator + =

Dodaje do tego `CSize`rozmiaru.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize:: operator-=

Odejmuje rozmiar od tego `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize:: operator +

Te operatory dodają `CSize` tę wartość do wartości parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Uwagi

Zobacz następujące opisy poszczególnych operatorów:

- **operator + (** *rozmiar* **)**

  Ta operacja dodaje dwie `CSize` wartości.

- **operator + (** *punkt* **)**

  Ta operacja przesunie (przenosi) wartość [punktu](/previous-versions/dd162805\(v=vs.85\)) (lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) przez tę `CSize` wartość. `cx` I `x` elementyczłonkowskie`POINT` tej `CSize` wartości są dodawane do elementów członkowskich danych `y`i. `cy` Jest on analogiczny do wersji [CPoint:: operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) , która przyjmuje parametr [size](/windows/win32/api/windef/ns-windef-size) .

- **operator + (** *lpRect* **)**

   Ta operacja przesunie (przenosi) wartość [Rect](/previous-versions/dd162897\(v=vs.85\)) (lub [CRect](../../atl-mfc-shared/reference/crect-class.md)) o tę `CSize` wartość. `left` `top` `bottom` `right`I elementy członkowskie tej wartościsą`RECT` dodawane do elementów członkowskich danych,,, i. `CSize` `cy` `cx` Jest on analogiczny do wersji [CRect:: operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) , która przyjmuje parametr [size](/windows/win32/api/windef/ns-windef-size) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize:: operator-

Pierwsze trzy z tych operatorów odejmuje tę `CSize` wartość do wartości parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Czwarty operator, jednoargumentowy minus, zmienia znak `CSize` wartości. Zobacz następujące opisy poszczególnych operatorów:

- **operator — (** *rozmiar* **)**

  Ta operacja odejmuje dwie `CSize` wartości.

- **operator-(** *punkt* **)**

  Ta operacja przesunie (przenosi) wartość [Point](/previous-versions/dd162805\(v=vs.85\)) lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) przez dodatek odwrotny do tej `CSize` wartości. `x` `y` Wartość `cx` i `cy` tej `POINT` wartości są odejmowane od elementów członkowskich danych i. `CSize` Jest on analogiczny do wersji elementu [CPoint:: operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) , który pobiera parametr [size](/windows/win32/api/windef/ns-windef-size) .

- **operator-(** *lpRect* **)**

  Ta operacja przesunie (przenosi) wartość [Rect](/previous-versions/dd162897\(v=vs.85\)) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) przez dodatek odwrotny do tej `CSize` wartości. `left` `right` `top` `bottom` I elementy członkowskie tej wartościsą`RECT` odejmowane od elementów członkowskich danych,, i. `CSize` `cy` `cx` Jest on analogiczny do wersji elementu [CRect:: operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-) , który pobiera parametr [size](/windows/win32/api/windef/ns-windef-size) .

- **operator-()**

  Ta operacja zwraca dodatek do `CSize` wartości odwrotnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint, klasa](../../atl-mfc-shared/reference/cpoint-class.md)
