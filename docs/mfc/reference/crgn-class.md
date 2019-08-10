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
ms.openlocfilehash: 66721f34a8ac2b6dac6addcfa04a88b46a37ee60
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916827"
---
# <a name="crgn-class"></a>Klasa CRgn

Hermetyzuje region interfejsu urządzenia graficznego systemu Windows (GDI).

## <a name="syntax"></a>Składnia

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn:: CRgn](#crgn)|Konstruuje `CRgn` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn:: CombineRgn](#combinergn)|Ustawia obiekt tak, aby był równoważny z złożeniem dwóch określonych `CRgn` obiektów. `CRgn`|
|[CRgn:: CopyRgn](#copyrgn)|Ustawia obiekt tak, aby był to kopia określonego `CRgn` obiektu. `CRgn`|
|[CRgn:: CreateEllipticRgn](#createellipticrgn)|`CRgn` Inicjuje obiekt z regionem eliptycznym.|
|[CRgn:: CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicjuje obiekt z regionem eliptycznego zdefiniowanym przez strukturę [Rect.](/windows/desktop/api/windef/ns-windef-tagrect) `CRgn`|
|[CRgn:: CreateFromData](#createfromdata)|Tworzy region z danego regionu i danych transformacji.|
|[CRgn:: CreateFromPath](#createfrompath)|Tworzy region na podstawie ścieżki wybranej w danym kontekście urządzenia.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|`CRgn` Inicjuje obiekt z wielobokówowym regionem. System automatycznie zamknie Wielokąt, w razie potrzeby, rysując linię od ostatniego wierzchołka do pierwszego.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|`CRgn` Inicjuje obiekt z regionem składającym się z serii zamkniętych wielokątów. Wielokąty mogą być rozłączane lub mogą się nakładać.|
|[CRgn:: CreateRectRgn](#createrectrgn)|`CRgn` Inicjuje obiekt z prostokątnym regionem.|
|[CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)|Inicjuje obiekt z prostokątnym regionem zdefiniowanym przez strukturę [Rect.](/windows/desktop/api/windef/ns-windef-tagrect) `CRgn`|
|[CRgn:: CreateRoundRectRgn](#createroundrectrgn)|`CRgn` Inicjuje obiekt z prostokątnym regionem z zaokrąglonymi rogami.|
|[CRgn:: EqualRgn](#equalrgn)|Sprawdza dwa `CRgn` obiekty, aby określić, czy są one równoważne.|
|[CRgn:: FromHandle](#fromhandle)|Zwraca wskaźnik do `CRgn` obiektu, gdy ma dojść do regionu systemu Windows.|
|[CRgn:: GetRegionData](#getregiondata)|Wypełnia określony bufor danymi opisującymi dany region.|
|[CRgn:: GetRgnBox](#getrgnbox)|Pobiera współrzędne prostokąta `CRgn` związanego z obiektem.|
|[CRgn:: OffsetRgn](#offsetrgn)|`CRgn` Przenosi obiekt o określone przesunięcia.|
|[CRgn::P tInRegion](#ptinregion)|Określa, czy określony punkt znajduje się w regionie.|
|[CRgn:: RectInRegion](#rectinregion)|Określa, czy jakakolwiek część określonego prostokąta znajduje się w granicach regionu.|
|[CRgn:: SetRectRgn](#setrectrgn)|`CRgn` Ustawia obiekt do określonego prostokątnego regionu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|Zwraca dojście systemu Windows zawarte w `CRgn` obiekcie.|

## <a name="remarks"></a>Uwagi

Region jest obszarem eliptycznym lub wielokąta w oknie. Aby użyć regionów, użyj funkcji składowych klasy `CRgn` z funkcjami przycinania zdefiniowanymi jako elementy członkowskie klasy. `CDC`

Funkcje składowe programu `CRgn` tworzą, zmieniają i pobierają informacje o obiekcie region, dla którego są wywoływane.

Aby uzyskać więcej informacji o `CRgn`używaniu programu, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="combinergn"></a>CRgn:: CombineRgn

Tworzy nowy region GDI przez połączenie dwóch istniejących regionów.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Parametry

*pRgn1*<br/>
Identyfikuje istniejący region.

*pRgn2*<br/>
Identyfikuje istniejący region.

*nCombineMode*<br/>
Określa operację, która ma zostać wykonana podczas łączenia dwóch regionów źródłowych. Może to być jedna z następujących wartości:

- RGN_AND używa nakładających się obszarów obu regionów (część wspólna).

- RGN_COPY tworzy kopię regionu 1 (identyfikowaną przez *pRgn1*).

- RGN_DIFF tworzy region składający się z obszarów regionu 1 (identyfikowanych przez *pRgn1*), które nie są częścią regionu 2 (identyfikowanego przez *pRgn2*).

- RGN_OR łączy oba regiony w całości (Unia).

- RGN_XOR łączy oba regiony, ale usuwa nakładające się obszary.

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu będącego wynikiem. Może to być jedna z następujących wartości:

- Nowy region COMPLEXREGION ma nakładające się obramowania.

- BŁĄD nie utworzono nowego regionu.

- NULLREGION nowy region jest pusty.

- SIMPLEREGION nowy region nie ma nakładających się obramowań.

### <a name="remarks"></a>Uwagi

Regiony są łączone w sposób określony przez *nCombineMode*.

Dwa określone regiony są łączone, a dojście w regionie jest przechowywane w `CRgn` obiekcie. W ten sposób każdy region jest przechowywany w `CRgn` obiekcie jest zastępowany przez połączony region.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Użyj [CopyRgn](#copyrgn) , aby po prostu skopiować jeden region do innego regionu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>CRgn:: CopyRgn

Kopiuje region zdefiniowany przez *pRgnSrc* do `CRgn` obiektu.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parametry

*pRgnSrc*<br/>
Identyfikuje istniejący region.

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu będącego wynikiem. Może to być jedna z następujących wartości:

- Nowy region COMPLEXREGION ma nakładające się obramowania.

- BŁĄD nie utworzono nowego regionu.

- NULLREGION nowy region jest pusty.

- SIMPLEREGION nowy region nie ma nakładających się obramowań.

### <a name="remarks"></a>Uwagi

Nowy region zastępuje region dawniej przechowywany w `CRgn` obiekcie. Ta funkcja jest szczególnym przypadkiem funkcji składowej [CombineRgn](#combinergn) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRgn:: CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>CRgn:: CreateEllipticRgn

Tworzy region eliptyczny.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa logiczną współrzędną x lewego górnego rogu wielokropka.

*y1*<br/>
Określa logiczną współrzędną y lewego górnego rogu prostokąta obwiedni.

*x2*<br/>
Określa logiczną współrzędną x dolnego prawego dolnego rogu elipsy.

*Y2*<br/>
Określa logiczną współrzędną y dolnego prawego dolnego rogu elipsy.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest definiowany przez prostokąt ograniczający określony przez *x1*, *Y1*, *X2*i *Y2*. Region jest przechowywany w `CRgn` obiekcie.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Po zakończeniu korzystania z regionu utworzonego za `CreateEllipticRgn` pomocą funkcji aplikacja powinna wybrać region z kontekstu urządzenia i `DeleteObject` użyć funkcji, aby ją usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>CRgn:: CreateEllipticRgnIndirect

Tworzy region eliptyczny.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje na `RECT` strukturę `CRect` lub obiekt, który zawiera współrzędne logiczne lewego górnego i prawego dolnego rogu prostokąta.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest zdefiniowany przez strukturę lub obiekt wskazywany przez *lpRect* i jest przechowywany w `CRgn` obiekcie.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Po zakończeniu korzystania z regionu utworzonego za `CreateEllipticRgnIndirect` pomocą funkcji aplikacja powinna wybrać region z kontekstu urządzenia i `DeleteObject` użyć funkcji, aby ją usunąć.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRgn:: CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>CRgn:: CreateFromData

Tworzy region z danego regionu i danych transformacji.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parametry

*lpXForm*<br/>
Wskazuje strukturę danych [Xform](/windows/desktop/api/wingdi/ns-wingdi-tagxform) , która definiuje transformację do wykonania w regionie. Jeśli ten wskaźnik ma wartość NULL, zostanie użyta transformacja tożsamości.

*nCount*<br/>
Określa liczbę bajtów wskazywanych przez *pRgnData*.

*pRgnData*<br/>
Wskazuje strukturę danych [rgnData](/windows/desktop/api/wingdi/ns-wingdi-rgndata) , która zawiera dane regionu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może pobrać dane dla regionu przez wywołanie `CRgn::GetRegionData` funkcji.

##  <a name="createfrompath"></a>CRgn:: CreateFromPath

Tworzy region na podstawie ścieżki wybranej w danym kontekście urządzenia.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identyfikuje kontekst urządzenia, który zawiera ścieżkę zamkniętą.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Kontekst urządzenia identyfikowany przez parametr *PDC* musi zawierać ścieżkę zamkniętą. Po `CreateFromPath` przekonwertowaniu ścieżki do regionu system Windows odrzuca ścieżkę zamkniętą z kontekstu urządzenia.

##  <a name="createpolygonrgn"></a>CRgn:: CreatePolygonRgn

Tworzy region wielokąta.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Wskazuje tablicę `POINT` struktur lub `CPoint` tablicę obiektów. Każda struktura Określa współrzędną x i Współrzędne y jednego wierzchołka wielokąta. `POINT` Struktura ma następującą postać:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Określa liczbę `POINT` struktur lub `CPoint` obiektów w tablicy wskazywanych przez *lpPoints*.

*nMode*<br/>
Określa tryb wypełniania dla regionu. Ten parametr może być ALTERNATYWą lub ZAMKNIĘCIEm.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

System automatycznie zamknie Wielokąt, w razie potrzeby, rysując linię od ostatniego wierzchołka do pierwszego. Ten region jest przechowywany w `CRgn` obiekcie.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Gdy tryb wypełniania wielokątów jest ALTERNATYWny, system wypełnia obszar między nieparzystymi i parzystymi krawędziami w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszą i drugą stroną, między trzecią i czwartą stroną itd.

Gdy tryb wypełniania wielokątów jest ZAWIJAny, system używa kierunku, w którym rysowany jest rysunek, aby określić, czy ma zostać wypełniony obszar. Każdy segment linii w wielokąta jest rysowany w trybie w prawo lub w lewo. Za każdym razem, gdy linia urojona rysowana od obszaru zamkniętego do zewnątrz przechodzą przez segment linii w prawo, liczba jest zwiększana. Gdy linia przechodzi przez segment linii w lewo, licznik jest zmniejszany. Obszar jest wypełniany, jeśli liczba jest różna od zera, gdy linia osiągnie się poza rysunkiem.

Gdy aplikacja została ukończona przy użyciu regionu utworzonego za pomocą `CreatePolygonRgn` funkcji, powinien wybrać region z kontekstu urządzenia i `DeleteObject` użyć funkcji, aby ją usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>CRgn:: CreatePolyPolygonRgn

Tworzy region składający się z serii zamkniętych wielokątów.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Wskazuje tablicę `POINT` struktur lub `CPoint` tablicę obiektów, która definiuje wierzchołki wielokątów. Każdy Wielokąt musi być jawnie zamknięty, ponieważ system nie zamyka ich automatycznie. Wielokąty są określane po kolei. `POINT` Struktura ma następującą postać:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Wskazuje tablicę liczb całkowitych. Pierwsza liczba całkowita określa liczbę wierzchołków w pierwszym wielokąta w tablicy *lpPoints* , drugą liczbę całkowitą określa liczbę wierzchołków w drugim wielokąta itd.

*nCount*<br/>
Określa łączną liczbę liczb całkowitych w tablicy *lpPolyCounts* .

*nPolyFillMode*<br/>
Określa tryb wypełniania wielokątów. Ta wartość może być ALTERNATYWą lub ZAMKNIĘCIEm.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten region jest przechowywany w `CRgn` obiekcie.

Wielokąty mogą być rozłączane lub mogą się nakładać.

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Gdy tryb wypełniania wielokątów jest ALTERNATYWny, system wypełnia obszar między nieparzystymi i parzystymi krawędziami w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszą i drugą stroną, między trzecią i czwartą stroną itd.

Gdy tryb wypełniania wielokątów jest ZAWIJAny, system używa kierunku, w którym rysowany jest rysunek, aby określić, czy ma zostać wypełniony obszar. Każdy segment linii w wielokąta jest rysowany w trybie w prawo lub w lewo. Za każdym razem, gdy linia urojona rysowana od obszaru zamkniętego do zewnątrz przechodzą przez segment linii w prawo, liczba jest zwiększana. Gdy linia przechodzi przez segment linii w lewo, licznik jest zmniejszany. Obszar jest wypełniany, jeśli liczba jest różna od zera, gdy linia osiągnie się poza rysunkiem.

Gdy aplikacja została ukończona przy użyciu regionu utworzonego za pomocą `CreatePolyPolygonRgn` funkcji, należy wybrać region z kontekstu urządzenia i użyć funkcji [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) , aby ją usunąć.

##  <a name="createrectrgn"></a>CRgn:: CreateRectRgn

Tworzy prostokątny region, który jest przechowywany w `CRgn` obiekcie.

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

*Y2*<br/>
Określa logiczną współrzędną y w prawym dolnym rogu regionu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Po zakończeniu korzystania z regionu utworzonego przez `CreateRectRgn`program, aby usunąć region, aplikacja powinna używać funkcji członkowskiej [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CRgn:: CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>CRgn:: CreateRectRgnIndirect

Tworzy prostokątny region, który jest przechowywany w `CRgn` obiekcie.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje strukturę lub `CRect` obiekt, który zawiera współrzędne logiczne lewego górnego i prawego dolnego rogu regionu. `RECT` `RECT` Struktura ma następującą postać:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Po zakończeniu korzystania z regionu utworzonego przez `CreateRectRgnIndirect`program, aby usunąć region, aplikacja powinna używać funkcji członkowskiej [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>CRgn:: CreateRoundRectRgn

Tworzy prostokątny region z zaokrąglonymi rogami, które są przechowywane `CRgn` w obiekcie.

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

*Y2*<br/>
Określa logiczną współrzędną y w prawym dolnym rogu regionu.

*x3*<br/>
Określa szerokość elipsy używanej do tworzenia zaokrąglonych rogów.

*Y3*<br/>
Określa wysokość elipsy używanej do tworzenia zaokrąglonych rogów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostek logicznych lub 64 KB pamięci, w zależności od tego, co jest mniejsze.

Gdy aplikacja została ukończona przy użyciu regionu utworzonego za pomocą `CreateRoundRectRgn` funkcji, należy wybrać region z kontekstu urządzenia i użyć funkcji [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) , aby ją usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>CRgn:: CRgn

Konstruuje `CRgn` obiekt.

```
CRgn();
```

### <a name="remarks"></a>Uwagi

Element członkowski `CRgn` danych nie zawiera prawidłowego regionu GDI systemu Windows, dopóki obiekt nie zostanie zainicjowany przy użyciu co najmniej jednej z innych funkcji Członkowskich. `m_hObject`

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRgn:: CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>CRgn:: EqualRgn

Określa, czy dany region jest odpowiednikiem regionu przechowywanego w `CRgn` obiekcie.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parametry

*pRgn*<br/>
Identyfikuje region.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli dwa regiony są równoważne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>CRgn:: FromHandle

Zwraca wskaźnik do `CRgn` obiektu, gdy ma dojść do regionu systemu Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parametry

*hRgn*<br/>
Określa uchwyt do regionu systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRgn` obiektu. Jeśli funkcja zakończyła się niepowodzeniem, zwracana wartość ma wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie jest jeszcze dołączony do dojścia, tworzony jest obiekt `CRgn` tymczasowy i jest on dołączony. `CRgn` Ten obiekt `CRgn` tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem wymawiania tego jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

##  <a name="getregiondata"></a>CRgn:: GetRegionData

Wypełnia określony bufor danymi opisującymi region.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parametry

*lpRgnData*<br/>
Wskazuje strukturę danych [rgnData](/windows/desktop/api/wingdi/ns-wingdi-rgndata) , która otrzymuje informacje. Jeśli ten parametr ma wartość NULL, wartość zwracana zawiera liczbę bajtów wymaganych dla danych regionu.

*nCount*<br/>
Określa rozmiar (w bajtach) bufora *lpRgnData* .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie i *nCount* określa odpowiednią liczbę bajtów, zwracana wartość jest zawsze *nCount*. Jeśli funkcja nie powiedzie się lub jeśli *nCount* określa mniejszą liczbę bajtów, wartość zwracana to 0 (błąd).

### <a name="remarks"></a>Uwagi

Te dane obejmują wymiary prostokątów składających się na region. Ta funkcja jest używana w połączeniu z `CRgn::CreateFromData` funkcją.

##  <a name="getrgnbox"></a>CRgn:: GetRgnBox

Pobiera współrzędne prostokąta `CRgn` związanego z obiektem.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje strukturę lub `CRect` obiekt, aby otrzymywać współrzędne prostokąta ograniczenia. `RECT` `RECT` Struktura ma następującą postać:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu. Może to być dowolna z następujących wartości:

- Region COMPLEXREGION ma nakładające się obramowania.

- Region NULLREGION jest pusty.

- Obiekt `CRgn` Error nie określa prawidłowego regionu.

- Region SIMPLEREGION nie ma nakładających się obramowań.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRgn:: CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>CRgn:: OffsetRgn

Przenosi region przechowywany w `CRgn` obiekcie o określone przesunięcia.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa liczbę jednostek do przeniesienia w lewo lub w prawo.

*y*<br/>
Określa liczbę jednostek, które mają zostać przesunięte w górę lub w dół.

*moment*<br/>
Współrzędna x *punktu* określa liczbę jednostek do przeniesienia w lewo lub w prawo. Współrzędna y *punktu* określa liczbę jednostek do przeniesienia w górę lub w dół. Parametr *Point* może być `POINT` strukturą lub `CPoint` obiektem.

### <a name="return-value"></a>Wartość zwracana

Typ nowego regionu. Może to być jedna z następujących wartości:

- Region COMPLEXREGION ma nakładające się obramowania.

- Dojście do regionu błędu jest nieprawidłowe.

- Region NULLREGION jest pusty.

- Region SIMPLEREGION nie ma nakładających się obramowań.

### <a name="remarks"></a>Uwagi

Funkcja przenosi jednostki *x* regionu wzdłuż osi x i *y* wzdłuż osi y.

Wartości współrzędnych regionu muszą być mniejsze niż lub równe 32 767 i większe niż lub równe-32 768. Parametry *x* i *y* muszą być starannie wybrane, aby zapobiec nieprawidłowym współrzędnymi regionów.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRgn:: CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>CRgn:: operator HRGN

Użyj tego operatora, aby uzyskać dojście `CRgn` do dołączonego interfejsu GDI systemu Windows.

```
operator HRGN() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows `CRgn` reprezentowane przez obiekt; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HRGN.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiekty graficzne](/windows/desktop/gdi/graphic-objects) w Windows SDK.

##  <a name="ptinregion"></a>CRgn::P tInRegion

Sprawdza, czy punkt określony przez *x* i *y* znajduje się w regionie `CRgn` przechowywanym w obiekcie.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określa logiczną współrzędną x punktu do przetestowania.

*y*<br/>
Określa logiczną współrzędną y punktu do przetestowania.

*moment*<br/>
Współrzędne x i y *punktu* określają współrzędne x i y punktu, w którym ma zostać przetestowana wartość. Parametr *Point* może być `POINT` strukturą lub `CPoint` obiektem.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli punkt znajduje się w regionie; w przeciwnym razie 0.

##  <a name="rectinregion"></a>CRgn:: RectInRegion

Określa, czy jakakolwiek część prostokąta określona przez *lpRect* znajduje się w granicach regionu przechowywanego w `CRgn` obiekcie.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje strukturę lub `CRect`obiekt. `RECT` `RECT` Struktura ma następującą postać:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli jakakolwiek część określonego prostokąta znajduje się w granicach regionu; w przeciwnym razie 0.

##  <a name="setrectrgn"></a>CRgn:: SetRectRgn

Tworzy region prostokątny.

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
Określa współrzędną x lewego górnego rogu prostokąta.

*y1*<br/>
Określa współrzędną y lewego górnego rogu prostokąta.

*x2*<br/>
Określa współrzędną x w prawym dolnym rogu prostokątnego obszaru.

*Y2*<br/>
Określa współrzędną y prawego dolnego rogu prostokątnego obszaru.

*lpRect*<br/>
Określa region prostokątny. Może być wskaźnikiem do `RECT` struktury `CRect` lub obiektu.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do [CreateRectRgn](#createrectrgn), jednak nie przydziela żadnej dodatkowej pamięci ze sterty aplikacji lokalnych systemu Windows. Zamiast tego używa miejsca przydzieloną dla regionu przechowywanego w `CRgn` obiekcie. Oznacza to, że `CRgn` obiekt musi już być zainicjowany z prawidłowym regionem systemu Windows przed `SetRectRgn`wywołaniem. Punkty podane przez *x1*, *Y1*, *X2*i *Y2* określają minimalny rozmiar przydzielonego miejsca.

Użyj tej funkcji zamiast funkcji członkowskiej, `CreateRectRgn` aby uniknąć wywołań Menedżera pamięci lokalnej.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
