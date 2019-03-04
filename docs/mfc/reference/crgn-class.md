---
title: Klasa CRgn
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 54018c3d59fe3d7e3d7a5062cda9b40da4f5d586
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279379"
---
# <a name="crgn-class"></a>Klasa CRgn

Hermetyzuje region Windows graphics urządzenia interface (GDI).

## <a name="syntax"></a>Składnia

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Konstruuje `CRgn` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Zestawy `CRgn` obiekt jest odpowiednikiem sumę dwóch określonych `CRgn` obiektów.|
|[CRgn::CopyRgn](#copyrgn)|Zestawy `CRgn` obiekt jest kopię określonego `CRgn` obiektu.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicjuje `CRgn` obiektu z regionem elipsy.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicjuje `CRgn` obiektu z regionem eliptycznego zdefiniowane przez [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.|
|[CRgn::CreateFromData](#createfromdata)|Tworzy obszar z danego regionu i przekształcania danych.|
|[CRgn::CreateFromPath](#createfrompath)|Tworzy obszar ze ścieżki, który wybrano w kontekście danego urządzenia.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicjuje `CRgn` obiektu za pomocą wielokątne obszaru. System wielokąta zostanie automatycznie zamknięte, jeśli to konieczne, za pomocą rysowania linii z ostatnim wierzchołku do pierwszej.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicjuje `CRgn` obiektu z regionem składający się z szeregu zamkniętych wielokątów. Wielokąty mogą być rozłączne lub mogą się nakładać.|
|[CRgn::CreateRectRgn](#createrectrgn)|Inicjuje `CRgn` obiektu z prostokątny obszar.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicjuje `CRgn` obiektu z prostokątny obszar zdefiniowany przez [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicjuje `CRgn` obiektu z prostokątny obszar z zaokrąglonymi rogami.|
|[CRgn::EqualRgn](#equalrgn)|Sprawdza, czy dwa `CRgn` obiektów, aby ustalić, czy są równoważne.|
|[CRgn::FromHandle](#fromhandle)|Zwraca wskaźnik do `CRgn` obiektu, kiedy podane dojście do regionu Windows.|
|[CRgn::GetRegionData](#getregiondata)|Wstawia określony bufor dane opisujące danego regionu.|
|[CRgn::GetRgnBox](#getrgnbox)|Pobiera współrzędne prostokąt otaczający `CRgn` obiektu.|
|[CRgn::OffsetRgn](#offsetrgn)|Przenosi `CRgn` obiektu przez określonych przesunięć.|
|[CRgn::PtInRegion](#ptinregion)|Określa, czy określony punkt znajduje się w regionie.|
|[CRgn::RectInRegion](#rectinregion)|Określa, czy jakakolwiek część określonego prostokąta znajduje się w granicach regionu.|
|[CRgn::SetRectRgn](#setrectrgn)|Zestawy `CRgn` obiekt do określonego regionu prostokątny.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn::operator hrgn —](#operator_hrgn)|Zwraca uchwyt Windows znajdujących się w `CRgn` obiektu.|

## <a name="remarks"></a>Uwagi

Region jest obszar eliptyczne lub wielokątne, w tym oknie. Aby używać regionów, należy użyć funkcji elementów członkowskich klasy `CRgn` z funkcjami wycinka zdefiniowane jako elementy członkowskie klasy `CDC`.

Funkcje elementów członkowskich `CRgn` tworzenia, alter i pobierania informacji o obiekcie region, dla której są wywoływane.

Aby uzyskać więcej informacji na temat korzystania z `CRgn`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

Tworzy nowy region GDI przez połączenie dwóch istniejących regionach.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Parametry

*pRgn1*<br/>
Identyfikuje istniejącego regionu.

*pRgn2*<br/>
Identyfikuje istniejącego regionu.

*nCombineMode*<br/>
Określa operację do wykonania podczas łączenia źródła dwóch regionów. Może być jednym z następujących wartości:

- RGN_AND używa nakładających się obszarów oba regiony (część wspólną).

- RGN_COPY tworzy kopię regionu 1 (identyfikowane przez *pRgn1*).

- RGN_DIFF tworzy obszar, składający się z obszarów regionu 1 (identyfikowane przez *pRgn1*) nie są częścią regionie 2 (identyfikowane przez *pRgn2*).

- RGN_OR łączy w sobie oba regiony w całości (Unia).

- RGN_XOR łączy obu regionów, ale usuwa obszary nakładających się.

### <a name="return-value"></a>Wartość zwracana

Określa typ wynikowy regionu. Może to być jedna z następujących wartości:

- COMPLEXREGION nowy region ma nakładających się obramowań.

- Błąd utworzyć nie nowych regionów.

- NULLREGION nowego regionu jest pusta.

- SIMPLEREGION nowym regionie nie ma nakładające się obramowania.

### <a name="remarks"></a>Uwagi

Regiony są łączone zgodnie z określonym *nCombineMode*.

Dwa określone regiony są łączone, a wynikowy uchwyt regionu jest przechowywany w `CRgn` obiektu. W związku z tym, niezależnie od regionu jest przechowywany w `CRgn` obiektu jest zastępowany przez połączone regionu.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Użyj [CopyRgn](#copyrgn) po prostu skopiować jednego regionu do innego regionu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

Kopiuje region zdefiniowany przez *pRgnSrc* do `CRgn` obiektu.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parametry

*pRgnSrc*<br/>
Identyfikuje istniejącego regionu.

### <a name="return-value"></a>Wartość zwracana

Określa typ wynikowy regionu. Może to być jedna z następujących wartości:

- COMPLEXREGION nowy region ma nakładających się obramowań.

- Błąd utworzyć nie nowych regionów.

- NULLREGION nowego regionu jest pusta.

- SIMPLEREGION nowym regionie nie ma nakładające się obramowania.

### <a name="remarks"></a>Uwagi

Nowy region zastępuje region, w uprzednio przechowywane w `CRgn` obiektu. Ta funkcja jest szczególnym przypadkiem [CombineRgn](#combinergn) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

Tworzy eliptycznego regionu.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa logiczną współrzędną x lewego górnego rogu prostokąt otaczający elipsy.

*y1*<br/>
Określa logiczną współrzędną y lewego górnego rogu prostokąt otaczający elipsy.

*x2*<br/>
Określa logiczną współrzędną x w prawym dolnym rogu prostokąt otaczający elipsy.

*y2*<br/>
Określa logiczną współrzędną y prawego dolnego rogu prostokąt otaczający elipsy.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest definiowany przez prostokąt otaczający określony przez *x1*, *y1*, *x2*, i *y2*. Region jest przechowywany w `CRgn` obiektu.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Po zakończeniu przy użyciu obszarem, który został utworzony za pomocą `CreateEllipticRgn` funkcji, aplikacji należy wybrać region się kontekstu urządzenia i użyć `DeleteObject` funkcję, aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

Tworzy eliptycznego regionu.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera współrzędne logiczne lewym i prawym dolnym rogu prostokąt otaczający elipsy.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest zdefiniowana przez strukturę lub obiekt wskazywany przez *lprect —* i jest przechowywany w `CRgn` obiektu.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Po zakończeniu przy użyciu obszarem, który został utworzony za pomocą `CreateEllipticRgnIndirect` funkcji, aplikacji należy wybrać region się kontekstu urządzenia i użyć `DeleteObject` funkcję, aby go usunąć.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>  CRgn::CreateFromData

Tworzy obszar z danego regionu i przekształcania danych.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parametry

*lpXForm*<br/>
Wskazuje [XFORM](/windows/desktop/api/wingdi/ns-wingdi-tagxform) strukturę danych, która definiuje przekształcenie do wykonania w regionie. Jeśli ten wskaźnik ma wartość NULL, używana jest przekształcania tożsamości.

*nCount*<br/>
Określa liczbę bajtów wskazywany przez *pRgnData*.

*pRgnData*<br/>
Wskazuje [RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata) struktura danych, która zawiera dane regionu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może pobrać danych dla regionu, wywołując `CRgn::GetRegionData` funkcji.

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

Tworzy obszar ze ścieżki, który wybrano w kontekście danego urządzenia.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identyfikuje kontekst urządzenia, który zawiera ścieżkę zamknięte.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Kontekst urządzenia identyfikowane przez *kontrolera pDC* parametr musi zawierać ścieżkę zamkniętą. Po `CreateFromPath` konwertuje ścieżkę do regionu, Windows odrzuca wszystkie ścieżce zamknięte z kontekstu urządzenia.

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

Tworzy obszar wielokątne.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Wskazuje na tablicę `POINT` struktury lub tablicę `CPoint` obiektów. Każda struktura określa współrzędne x i y współrzędne jednego wierzchołka wielokąta. `POINT` Struktura ma następującą postać:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Określa liczbę `POINT` struktury lub `CPoint` obiektów w tablicy, wskazywana przez *lpPoints*.

*nMode*<br/>
Określa tryb wypełnianie dla regionu. Ten parametr może być ALTERNATYWNYM lub rozwiązanie.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

System wielokąta zostanie automatycznie zamknięte, jeśli to konieczne, za pomocą rysowania linii z ostatnim wierzchołku do pierwszej. Region wynikowe są przechowywane w `CRgn` obiektu.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Przy włączonym trybie wypełnianie wielokąta alternatywny, system wypełnia obszar między stronami nieparzystą i parzystych wielokąta w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszym i drugim po stronie, między strona trzecia i czwarta i tak dalej.

Gdy tryb wypełnianie Wielokąt jest rozwiązania, wówczas system używa kierunek, w którym rysunku została narysowana w celu ustalenia, czy wypełnił obszar. Każdy segment linii wielokąta jest rysowane w prawo lub wskazówek zegara. Zawsze, gdy wtedy linię pobrane z obszaru na zewnątrz rysunku przechodzi przez segment linii do ruchu wskazówek zegara, licznik jest zwiększany. Wiersz przejścia przez segment linii do ruchu wskazówek zegara, liczba zostanie zmniejszony. Obszar jest wypełniana, jeśli liczba jest różna od zera, gdy wiersz osiągnie poza rysunku.

Gdy aplikacja zakończy obszarem, który został utworzony za pomocą `CreatePolygonRgn` funkcji go powinien wybierz region, out kontekstu urządzenia i użyć `DeleteObject` funkcję, aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

Tworzy obszar składający się z szeregu zamkniętych wielokątów.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Wskazuje na tablicę `POINT` struktury lub tablicę `CPoint` obiektów, które definiuje wierzchołki wielokątów. Każdy Wielokąt musi być jawnie zamknięty, ponieważ system nie Zamknij je automatycznie. Wielokąty podano pod rząd. `POINT` Struktura ma następującą postać:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Wskazuje tablicy liczb całkowitych. Pierwsza liczba całkowita. określa liczbę wierzchołków w pierwszym wielokąta w *lpPoints* tablicy, a drugi liczbą całkowitą określa liczbę wierzchołki wielokąta drugi, i tak dalej.

*nCount*<br/>
Określa sumę liczb całkowitych *lpPolyCounts* tablicy.

*nPolyFillMode*<br/>
Określa tryb wypełnianie wielokąta. Ta wartość może być ALTERNATYWNYM lub rozwiązanie.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region wynikowe są przechowywane w `CRgn` obiektu.

Wielokąty mogą być rozłączne lub mogą się nakładać.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Przy włączonym trybie wypełnianie wielokąta alternatywny, system wypełnia obszar między stronami nieparzystą i parzystych wielokąta w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszym i drugim po stronie, między strona trzecia i czwarta i tak dalej.

Gdy tryb wypełnianie Wielokąt jest rozwiązania, wówczas system używa kierunek, w którym rysunku została narysowana w celu ustalenia, czy wypełnił obszar. Każdy segment linii wielokąta jest rysowane w prawo lub wskazówek zegara. Zawsze, gdy wtedy linię pobrane z obszaru na zewnątrz rysunku przechodzi przez segment linii do ruchu wskazówek zegara, licznik jest zwiększany. Wiersz przejścia przez segment linii do ruchu wskazówek zegara, liczba zostanie zmniejszony. Obszar jest wypełniana, jeśli liczba jest różna od zera, gdy wiersz osiągnie poza rysunku.

Gdy aplikacja zakończy obszarem, który został utworzony za pomocą `CreatePolyPolygonRgn` funkcji go powinien wybierz region, out kontekstu urządzenia i użyć [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcja elementu członkowskiego, aby go usunąć.

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

Tworzy prostokątny obszar, który jest przechowywany w `CRgn` obiektu.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa logiczną współrzędną x lewego górnego rogu regionu.

*y1*<br/>
Określa logiczną współrzędną y lewego górnego rogu regionu.

*x2*<br/>
Określa logiczną współrzędną x w prawym dolnym rogu regionu.

*y2*<br/>
Określa logiczną współrzędną y prawego dolnego rogu regionu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Po zakończeniu przy użyciu obszarem, który został utworzony przez `CreateRectRgn`, aplikacja powinna używać [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcja elementu członkowskiego, aby usunąć regionu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Na przykład dodatkowe zobacz [CRgn::CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

Tworzy prostokątny obszar, który jest przechowywany w `CRgn` obiektu.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera współrzędne logiczne lewym i prawym dolnym rogu regionu. `RECT` Struktura ma następującą postać:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Po zakończeniu przy użyciu obszarem, który został utworzony przez `CreateRectRgnIndirect`, aplikacja powinna używać [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcja elementu członkowskiego, aby usunąć regionu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

Tworzy kształcie prostokąta z zaokrąglonymi narożnikami, które są przechowywane w `CRgn` obiektu.

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa logiczną współrzędną x lewego górnego rogu regionu.

*y1*<br/>
Określa logiczną współrzędną y lewego górnego rogu regionu.

*x2*<br/>
Określa logiczną współrzędną x w prawym dolnym rogu regionu.

*y2*<br/>
Określa logiczną współrzędną y prawego dolnego rogu regionu.

*x3*<br/>
Określa szerokość elipsy pozwala utworzyć zaokrąglone rogi.

*y3*<br/>
Określa wysokość elipsy pozwala utworzyć zaokrąglone rogi.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, która kwota jest mniejsza.

Gdy aplikacja zakończy obszarem, który został utworzony za pomocą `CreateRoundRectRgn` funkcji go powinien wybierz region, out kontekstu urządzenia i użyć [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcja elementu członkowskiego, aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

Konstruuje `CRgn` obiektu.

```
CRgn();
```

### <a name="remarks"></a>Uwagi

`m_hObject` Element członkowski danych nie zawiera ważnym przekraczanym Windows GDI, dopóki obiekt jest inicjowany z co najmniej jeden z innych `CRgn` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>  CRgn::EqualRgn

Określa, czy w danym regionie jest odpowiednikiem region przechowywany w `CRgn` obiektu.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parametry

*pRgn*<br/>
Identyfikuje region.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dwa regiony są równoważne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>  CRgn::FromHandle

Zwraca wskaźnik do `CRgn` obiektu, kiedy podane dojście do regionu Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parametry

*hRgn*<br/>
Określa dojścia do obszaru Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRgn` obiektu. Jeśli funkcja zakończyła się niepowodzeniem, wartość zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CRgn` obiektu nie jest już dołączony do uchwyt tymczasowego `CRgn` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CRgn` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, w której czas wszystkich tymczasowych grafiki obiekty zostaną usunięte. Innymi słowy to to, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu w jednym oknie.

##  <a name="getregiondata"></a>  CRgn::GetRegionData

Wstawia określony bufor dane opisujące regionu.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parametry

*lpRgnData*<br/>
Wskazuje [RGNDATA](/windows/desktop/api/wingdi/ns-wingdi-_rgndata) struktury danych, która otrzymuje informacje. Jeśli ten parametr ma wartość NULL, wartość zwracana zawiera liczbę bajtów potrzebnych danych regionu.

*nCount*<br/>
Określa rozmiar w bajtach, *lpRgnData* buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie i *nCount* określa odpowiednią liczbą bajtów, wartość zwracana jest zawsze *nCount*. Jeśli funkcja zawiedzie, lub jeśli *nCount* określa mniejsza niż odpowiednią liczbę bajtów, wartość zwracana to 0 (błąd).

### <a name="remarks"></a>Uwagi

Te dane obejmują wymiary prostokątami, które składają się na region. Ta funkcja jest używana w połączeniu z `CRgn::CreateFromData` funkcji.

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

Pobiera współrzędne prostokąt otaczający `CRgn` obiektu.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiektu do odbierania współrzędne prostokąt otaczający. `RECT` Struktura ma następującą postać:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu. Może być dowolną z następujących wartości:

- COMPLEXREGION Region ma nakładających się obramowań.

- NULLREGION Region jest pusty.

- Błąd `CRgn` obiektu nie określa nieprawidłowy region.

- SIMPLEREGION regionie nie ma nakładające się obramowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

Przenosi region przechowywany w `CRgn` obiektu przez określonych przesunięć.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa liczbę jednostek, aby przesunąć w lewo lub w prawo.

*y*<br/>
Określa liczbę jednostek można przenieść w górę lub w dół.

*Punkt*<br/>
Współrzędną x *punktu* określa liczbę jednostek, aby przesunąć w lewo lub w prawo. Współrzędną y *punktu* określa liczbę jednostek można przenieść w górę lub w dół. *Punktu* parametru może być `POINT` struktury lub `CPoint` obiektu.

### <a name="return-value"></a>Wartość zwracana

Typ w nowym regionie. Może być jednym z następujących wartości:

- COMPLEXREGION Region ma nakładających się obramowań.

- Błąd Region dojście jest nieprawidłowe.

- NULLREGION Region jest pusty.

- SIMPLEREGION regionie nie ma nakładające się obramowania.

### <a name="remarks"></a>Uwagi

Funkcja przenosi region *x* jednostek wzdłuż osi x i *y* jednostki wzdłuż osi y.

Wartości współrzędnych regionu musi być mniejsza lub równa 32 767 i większa niż lub równa-32 768. *x* i *y* parametry należy ostrożnie wybierać zapobiegające współrzędne nieprawidłowy region.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>  CRgn::operator hrgn —

Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CRgn` obiektu.

```
operator HRGN() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, dojścia do obiektu Windows GDI reprezentowany przez `CRgn` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatora rzutowania, który obsługuje bezpośredniego użycia obiektu hrgn —.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

##  <a name="ptinregion"></a>  CRgn::PtInRegion

Sprawdza, czy punktu określonego przez właściwość *x* i *y* znajduje się w regionie, przechowywane w `CRgn` obiektu.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa logiczną współrzędną x punktu do testowania.

*y*<br/>
Określa logiczną współrzędną y punktu do testowania.

*Punkt*<br/>
- Współrzędnych x i y z *punktu* określić współrzędne x i y punktu do testowania wartości. *Punktu* parametru może być `POINT` struktury lub `CPoint` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli punkt znajduje się w regionie; w przeciwnym razie 0.

##  <a name="rectinregion"></a>  CRgn::RectInRegion

Określa, czy jakakolwiek część prostokąt określony przez *lprect —* znajduje się w granicach region przechowywany w `CRgn` obiektu.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiektu. `RECT` Struktura ma następującą postać:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli jakakolwiek część określonego prostokąta znajduje się w granicach regionu; w przeciwnym razie 0.

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

Tworzy prostokątny obszar.

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa współrzędną x w lewym górnym rogu prostokątny obszar.

*y1*<br/>
Określa współrzędną y lewego górnego rogu prostokątny obszar.

*x2*<br/>
Określa współrzędną x w prawym dolnym rogu prostokątny obszar.

*y2*<br/>
Określa współrzędną y prawego dolnego rogu prostokątny obszar.

*lpRect*<br/>
Określa prostokątny obszar. Może być wskaźnik do `RECT` struktury lub `CRect` obiektu.

### <a name="remarks"></a>Uwagi

W odróżnieniu od [CreateRectRgn](#createrectrgn), jednak ją nie przydziela żadnych dodatkowych pamięci lokalnej sterty aplikacji Windows. Zamiast tego używa miejsce przydzielone na region przechowywany w `CRgn` obiektu. Oznacza to, że `CRgn` obiektu muszą już zostały zainicjowane z ważnym przekraczanym Windows przed wywołaniem `SetRectRgn`. Punkty, określone przez *x1*, *y1*, *x2*, i *y2* określa minimalną wielkość przydzielonego miejsca.

Użyj tej funkcji, zamiast `CreateRectRgn` funkcja elementu członkowskiego, aby uniknąć wywołania do Menedżera pamięci lokalnej.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
