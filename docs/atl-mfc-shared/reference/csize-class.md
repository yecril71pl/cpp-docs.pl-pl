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
ms.openlocfilehash: 87beb468fb8fe61358a03e2cd287903a268a18ba
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740496"
---
# <a name="csize-class"></a>CSize, klasa

Podobnie jak Windows [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury, która implementuje współrzędne względne lub pozycję.

## <a name="syntax"></a>Składnia

```
class CSize : public tagSIZE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSize::CSize](#csize)|Konstruuje `CSize` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSize::operator-](#operator_-)|Odejmuje dwa rozmiary.|
|[CSize::operator! =](#operator_neq)|Sprawdza pod kątem nierówności pomiędzy `CSize` i rozmiar.|
|[CSize::operator +](#operator_add)|Dodaje dwa rozmiary.|
|[CSize::operator +=](#operator_add_eq)|Dodaje o rozmiarze do `CSize`.|
|[CSize::operator-=](#operator_-_eq)|Odejmuje o rozmiarze od `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Sprawdza pod kątem równości pomiędzy `CSize` i rozmiar.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną `SIZE` struktury. Oznacza to, że można przekazać `CSize` w parametrze wywołuje `SIZE` i składowych danych `SIZE` struktury są elementami członkowskimi dane dostępne `CSize`.

`cx` i `cy` członkowie `SIZE` (i `CSize`) były publiczne. Ponadto `CSize` implementuje elementów członkowskich do manipulowania `SIZE` struktury.

> [!NOTE]
> Aby uzyskać więcej informacji na temat udostępnionych klasy narzędzi (takich jak `CSize`), zobacz [udostępnionego klasy](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltypes.h

##  <a name="csize"></a>  CSize::CSize

Konstruuje `CSize` obiektu.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parametry

*initCX*<br/>
Zestawy `cx` członka `CSize`.

*initCY*<br/>
Zestawy `cy` członka `CSize`.

*initSize*<br/>
[ROZMIAR](/windows/desktop/api/windef/ns-windef-tagsize) struktury lub `CSize` obiektu użytego do zainicjowania `CSize`.

*initPt*<br/>
[PUNKT](/windows/desktop/api/windef/ns-windef-tagpoint) struktury lub `CPoint` obiektu użytego do zainicjowania `CSize`.

*dwSize*<br/>
DWORD używane do zainicjowania `CSize`. Word niskiego rzędu jest `cx` elementu członkowskiego i word wyższego rzędu jest `cy` elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Jeśli nie podano argumentów, `cx` i `cy` są inicjowane od zera.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator ==

Sprawdza, czy pod kątem równości pomiędzy dwoma rozmiarów.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość różną od zera, jeśli rozmiary są równe, otherwize 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator! =

Sprawdza, czy pod kątem nierówności pomiędzy dwoma rozmiarów.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość różną od zera, jeśli rozmiary nie są równe, w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator +=

Dodaje o rozmiarze do tego `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator-=

Odejmuje rozmiar tego `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

Dodaj te operatory `CSize` wartość do wartości parametru.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Uwagi

Zobacz poniższe opisy poszczególnych operatorach:

- **Operator + (** *rozmiar* **)**

  Ta operacja spowoduje dodanie dwóch `CSize` wartości.

- **Operator + (** *punktu* **)**

  Ta operacja powoduje przesunięcie (ruch) [punktu](/previous-versions/dd162805\(v=vs.85\)) (lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) wartość to `CSize` wartość. `cx` i `cy` członków tego `CSize` wartości są dodawane do `x` i `y` elementów członkowskich danych `POINT` wartość. Jest ono odpowiednikiem wersję [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) przyjmującej [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

- **Operator + (** *lprect —* **)**

   Ta operacja powoduje przesunięcie (ruch) [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) (lub [CRect](../../atl-mfc-shared/reference/crect-class.md)) wartość to `CSize` wartość. `cx` i `cy` członków tego `CSize` wartości są dodawane do `left`, `top`, `right`, i `bottom` elementów członkowskich danych `RECT` wartość. Jest ono odpowiednikiem wersję [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) przyjmującej [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator-

Pierwsze trzy te operatory odjąć to `CSize` wartość do wartości parametru.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Czwarty operatora jednoargumentowego znaku minusa, zmienia znak `CSize` wartość. Zobacz poniższe opisy poszczególnych operatorach:

- **Operator-(** *rozmiar* **)**

  Ta operacja odejmuje dwie `CSize` wartości.

- **Operator-(** *punktu* **)**

  Ta operacja powoduje przesunięcie (ruch) [punktu](/previous-versions/dd162805\(v=vs.85\)) lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) wartość przez odwrotność dodatku `CSize` wartość. `cx` i `cy` tego `CSize` wartości są odejmowane od `x` i `y` elementów członkowskich danych `POINT` wartość. Jest ono odpowiednikiem wersję [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) przyjmującej [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

- **Operator-(** *lprect —* **)**

  Ta operacja powoduje przesunięcie (ruch) [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) wartość przez odwrotność dodatku `CSize` wartość. `cx` i `cy` członków tego `CSize` wartości są odejmowane od `left`, `top`, `right`, i `bottom` elementów członkowskich danych `RECT` wartość. Jest ono odpowiednikiem wersję [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) przyjmującej [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) parametru.

- **operator-)**

  Ta operacja Zwraca odwrotność dodatku `CSize` wartość.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint, klasa](../../atl-mfc-shared/reference/cpoint-class.md)
