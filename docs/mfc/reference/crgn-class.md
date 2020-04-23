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
ms.openlocfilehash: e84526eec8f4fd4b1935fa39bc7f4ed3c4d5dd71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754479"
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
|[CRgn::CRgn](#crgn)|Konstruuje `CRgn` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn::Combinergn](#combinergn)|Ustawia `CRgn` obiekt tak, aby był odpowiednikiem `CRgn` unii dwóch określonych obiektów.|
|[CRgn::CopyRgn](#copyrgn)|Ustawia `CRgn` obiekt tak, aby był kopią określonego `CRgn` obiektu.|
|[CRgn::CreateEllipticrgn](#createellipticrgn)|Inicjuje `CRgn` obiekt z regionem eliptycznym.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicjuje `CRgn` obiekt z regionem eliptycznym zdefiniowanym przez strukturę [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateFromData](#createfromdata)|Tworzy region z danego regionu i danych transformacji.|
|[CRgn::CreateFromPath](#createfrompath)|Tworzy region ze ścieżki wybranej w danym kontekście urządzenia.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicjuje `CRgn` obiekt z regionem wielokątnym. System zamyka wielokąt automatycznie, jeśli to konieczne, rysując linię od ostatniego wierzchołka do pierwszego.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicjuje `CRgn` obiekt z regionem składającym się z serii zamkniętych wielokątów. Wielokąty mogą być rozłączne lub mogą się pokrywać.|
|[CRgn::CreateRectrgn](#createrectrgn)|Inicjuje `CRgn` obiekt z prostokątnym regionem.|
|[CRgn::CreateRectrgnIndirect](#createrectrgnindirect)|Inicjuje `CRgn` obiekt z prostokątnym regionem zdefiniowanym przez tructure [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateRoundRectrgn](#createroundrectrgn)|Inicjuje `CRgn` obiekt z prostokątnym obszarem z zaokrąglonymi narożnikami.|
|[CRgn::Equalrgn](#equalrgn)|Sprawdza `CRgn` dwa obiekty, aby ustalić, czy są one równoważne.|
|[CRgn::OdRążej](#fromhandle)|Zwraca wskaźnik do `CRgn` obiektu po podaniu dojścia do regionu systemu Windows.|
|[CRgn::GetRegionData](#getregiondata)|Wypełnia określony bufor danymi opisującymi dany region.|
|[CRgn::GetRgnBox](#getrgnbox)|Pobiera współrzędne prostokąta ograniczającego `CRgn` obiektu.|
|[CRgn::OffsetRgn](#offsetrgn)|Przenosi `CRgn` obiekt o określone odsunięcia.|
|[CRgn::PtRegion](#ptinregion)|Określa, czy określony punkt znajduje się w regionie.|
|[CRgn::RectInRegion](#rectinregion)|Określa, czy dowolna część określonego prostokąta znajduje się w granicach regionu.|
|[CRgn::SetRectrgn](#setrectrgn)|Ustawia `CRgn` obiekt na określony prostokątny obszar.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRgn::operator HRGN](#operator_hrgn)|Zwraca uchwyt systemu Windows `CRgn` zawarty w obiekcie.|

## <a name="remarks"></a>Uwagi

Region jest obszarem eliptycznym lub wielokątnym w oknie. Aby użyć regionów, należy użyć funkcji `CRgn` członkowskich klasy z funkcjami `CDC`przycinania zdefiniowanymi jako członkowie klasy .

Funkcje członkowskie `CRgn` tworzenia, modyfikowania i pobierania informacji o obiekcie regionu, dla którego są wywoływane.

Aby uzyskać więcej `CRgn`informacji na temat używania programu , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::Combinergn

Tworzy nowy region GDI, łącząc dwa istniejące regiony.

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

*nKombinowaćmode*<br/>
Określa operację, która ma być wykonywana podczas łączenia dwóch regionów źródłowych. Może to być jedna z następujących wartości:

- RGN_AND Używa nakładających się obszarów obu regionów (przecięcia).

- RGN_COPY Tworzy kopię regionu 1 (identyfikowaną przez *pRgn1*).

- RGN_DIFF Tworzy region składający się z obszarów regionu 1 (oznaczonych za pomocą *pRgn1),* które nie są częścią regionu 2 (oznaczone przez *pRgn2*).

- RGN_OR Łączy oba regiony w całości (unia).

- RGN_XOR Łączy oba regiony, ale usuwa nakładające się obszary.

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu wynikowego. Może to być jedna z następujących wartości:

- COMPLEXREGION Nowy region ma nakładające się obramowania.

- BŁĄD Nie utworzono nowego regionu.

- NULLREGION Nowy region jest pusty.

- SIMPLEREGION Nowy region nie ma nakładających się granic.

### <a name="remarks"></a>Uwagi

Regiony są łączone zgodnie z *nCombineMode*.

Dwa określone regiony są łączone, a wynikowy `CRgn` dojście regionu jest przechowywany w obiekcie. W związku z tym `CRgn` niezależnie od regionu jest przechowywany w obiekcie jest zastępowany przez region połączony.

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Użyj [CopyRgn,](#copyrgn) aby po prostu skopiować jeden region do innego regionu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::CopyRgn

Kopiuje region zdefiniowany przez *pRgnSrc* do `CRgn` obiektu.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parametry

*pRgnSrc*<br/>
Identyfikuje istniejący region.

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu wynikowego. Może to być jedna z następujących wartości:

- COMPLEXREGION Nowy region ma nakładające się obramowania.

- BŁĄD Nie utworzono nowego regionu.

- NULLREGION Nowy region jest pusty.

- SIMPLEREGION Nowy region nie ma nakładających się granic.

### <a name="remarks"></a>Uwagi

Nowy region zastępuje region wcześniej przechowywany `CRgn` w obiekcie. Ta funkcja jest szczególnym przypadkiem funkcji elementu członkowskiego [CombineRgn.](#combinergn)

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::CreateEllipticrgn

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
Określa logiczną współrzędną x lewego górnego rogu prostokąta ograniczającego elipsy.

*y1*<br/>
Określa logiczną współrzędną y lewego górnego rogu prostokąta ograniczającego elipsy.

*x2*<br/>
Określa logiczną współrzędną x w prawym dolnym rogu prostokąta ograniczającego elipsy.

*y2*<br/>
Określa logiczną współrzędną y w prawym dolnym rogu prostokąta ograniczającego elipsy.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest definiowany przez prostokąt ograniczający określony przez *x1*, *y1*, *x2*i *y2*. Region jest przechowywany `CRgn` w obiekcie.

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Po zakończeniu korzystania z regionu `CreateEllipticRgn` utworzonego za pomocą funkcji, aplikacja powinna wybrać `DeleteObject` region z kontekstu urządzenia i użyć funkcji, aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Tworzy region eliptyczny.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje na `RECT` strukturę `CRect` lub obiekt zawierający współrzędne logiczne lewego górnego i prawego dolnego rogu prostokąta ograniczającego elipsy.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Region jest zdefiniowany przez strukturę lub obiekt wskazany przez `CRgn` *lpRect* i jest przechowywany w obiekcie.

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Po zakończeniu korzystania z regionu `CreateEllipticRgnIndirect` utworzonego za pomocą funkcji, aplikacja powinna wybrać `DeleteObject` region z kontekstu urządzenia i użyć funkcji, aby go usunąć.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::CreateFromData

Tworzy region z danego regionu i danych transformacji.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parametry

*lpXForm (lpXForm)*<br/>
Wskazuje strukturę [XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata, która definiuje transformację, która ma być wykonywana w regionie. Jeśli ten wskaźnik ma wartość NULL, używana jest transformacja tożsamości.

*Ncount*<br/>
Określa liczbę bajtów wskazywali przez *pRgnData*.

*pRgnData*<br/>
Wskazuje strukturę danych [RGNDATA,](/windows/win32/api/wingdi/ns-wingdi-rgndata) która zawiera dane regionu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może pobierać dane dla regionu, wywołując `CRgn::GetRegionData` funkcję.

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::CreateFromPath

Tworzy region ze ścieżki wybranej w danym kontekście urządzenia.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Identyfikuje kontekst urządzenia, który zawiera zamkniętą ścieżkę.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Kontekst urządzenia identyfikowany przez parametr *pDC* musi zawierać zamkniętą ścieżkę. Po `CreateFromPath` przekonwertowaniu ścieżki na region system Windows odrzuca zamkniętą ścieżkę z kontekstu urządzenia.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn

Tworzy region wielokątny.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parametry

*lpPunkty*<br/>
Wskazuje tablicę `POINT` struktur lub tablicę `CPoint` obiektów. Każda struktura określa współrzędną x i współrzędną y jednego wierzchołka wielokąta. Struktura `POINT` ma następującą formę:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*Ncount*<br/>
Określa liczbę `POINT` struktur lub `CPoint` obiektów w tablicy wskazywionej przez punkty *lp*.

*nMode*<br/>
Określa tryb napełniania dla regionu. Ten parametr może być alternatywny lub nawijany.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

System zamyka wielokąt automatycznie, jeśli to konieczne, rysując linię od ostatniego wierzchołka do pierwszego. Wynikowy region jest przechowywany `CRgn` w obiekcie.

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Gdy tryb wypełniania wielokątów jest alternatywny, system wypełnia obszar między nieparzystymi i parzystymi bokami wielokątów w każdej linii skanowania. Oznacza to, że system wypełnia obszar między pierwszą i drugą stroną, między trzecią i czwartą stroną i tak dalej.

Gdy tryb wypełniania wielokąta jest KRĘTY, system używa kierunku, w którym rysowano figurę, aby określić, czy wypełnić obszar. Każdy segment linii w wielokąt jest rysowany w kierunku zgodnym z ruchem wskazówek zegara lub w kierunku przeciwnym do ruchu wskazówek zegara. Za każdym razem, gdy wyimaginowana linia rysowana z zamkniętego obszaru na zewnątrz figury przechodzi przez segment linii zgodnie z ruchem wskazówek zegara, liczba jest zwiększana. Gdy linia przechodzi przez segment linii przeciwnej do ruchu wskazówek zegara, liczba jest zmniejszana. Obszar jest wypełniany, jeśli liczba jest niezerowa, gdy linia osiągnie zewnętrzną część rysunku.

Po zakończeniu aplikacji przy użyciu regionu utworzonego za `CreatePolygonRgn` pomocą funkcji, należy wybrać `DeleteObject` region z kontekstu urządzenia i użyć funkcji, aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn

Tworzy region składający się z serii zamkniętych wielokątów.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parametry

*lpPunkty*<br/>
Wskazuje tablicę `POINT` struktur lub tablicę `CPoint` obiektów definiuj wierzchołki wielokątów. Każdy wielokąt musi być jawnie zamknięty, ponieważ system nie zamyka ich automatycznie. Wielokąty są określane kolejno. Struktura `POINT` ma następującą formę:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Wskazuje tablicę liczby całkowitych. Pierwsza liczba całkowita określa liczbę wierzchołków w pierwszym wielokąta w *tablicy lpPoints,* druga liczba całkowita określa liczbę wierzchołków w drugim wielokącie i tak dalej.

*Ncount*<br/>
Określa całkowitą liczbę liczb całkowitych w *tablicy lpPolyCounts.*

*nPolyFillMode (Polski)*<br/>
Określa tryb wypełniania wielokątów. Wartość ta może być alternatywna lub nawijana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wynikowy region jest przechowywany `CRgn` w obiekcie.

Wielokąty mogą być rozłączne lub mogą się pokrywać.

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Gdy tryb wypełniania wielokątów jest alternatywny, system wypełnia obszar między nieparzystymi i parzystymi bokami wielokątów w każdej linii skanowania. Oznacza to, że system wypełnia obszar między pierwszą i drugą stroną, między trzecią i czwartą stroną i tak dalej.

Gdy tryb wypełniania wielokąta jest KRĘTY, system używa kierunku, w którym rysowano figurę, aby określić, czy wypełnić obszar. Każdy segment linii w wielokąt jest rysowany w kierunku zgodnym z ruchem wskazówek zegara lub w kierunku przeciwnym do ruchu wskazówek zegara. Za każdym razem, gdy wyimaginowana linia rysowana z zamkniętego obszaru na zewnątrz figury przechodzi przez segment linii zgodnie z ruchem wskazówek zegara, liczba jest zwiększana. Gdy linia przechodzi przez segment linii przeciwnej do ruchu wskazówek zegara, liczba jest zmniejszana. Obszar jest wypełniany, jeśli liczba jest niezerowa, gdy linia osiągnie zewnętrzną część rysunku.

Po zakończeniu aplikacji przy użyciu regionu utworzonego za pomocą `CreatePolyPolygonRgn` funkcji, należy wybrać region z kontekstu urządzenia i użyć [CGDIObject::DeleteObject funkcji członkowskiej,](../../mfc/reference/cgdiobject-class.md#deleteobject) aby go usunąć.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::CreateRectrgn

Tworzy prostokątny obszar, który jest `CRgn` przechowywany w obiekcie.

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
Określa logiczną współrzędną y w prawym dolnym rogu regionu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Po zakończeniu korzystania z regionu utworzonego przez `CreateRectRgn`aplikację należy użyć [CGDIObject::DeleteObject funkcji członkowskiej,](../../mfc/reference/cgdiobject-class.md#deleteobject) aby usunąć region.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CRgn::CombineRgn](#combinergn).

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::CreateRectrgnIndirect

Tworzy prostokątny obszar, który jest `CRgn` przechowywany w obiekcie.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę `RECT` `CRect` lub obiekt zawierający współrzędne logiczne lewego górnego i prawego dolnego rogu regionu. Struktura `RECT` ma następującą formę:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Po zakończeniu korzystania z regionu utworzonego przez `CreateRectRgnIndirect`aplikację należy użyć [CGDIObject::DeleteObject funkcji członkowskiej,](../../mfc/reference/cgdiobject-class.md#deleteobject) aby usunąć region.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::CreateRoundRectrgn

Tworzy prostokątny obszar z zaokrąglonymi `CRgn` narożnikami, który jest przechowywany w obiekcie.

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
Określa logiczną współrzędną y w prawym dolnym rogu regionu.

*x3*<br/>
Określa szerokość elipsy używanej do tworzenia zaokrąglonych narożników.

*3.*<br/>
Określa wysokość elipsy używanej do tworzenia zaokrąglonych narożników.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozmiar regionu jest ograniczony do 32 767 na 32 767 jednostek logicznych lub 64K pamięci, w zależności od tego, która z tych wartości jest mniejsza.

Po zakończeniu aplikacji przy użyciu regionu utworzonego za pomocą `CreateRoundRectRgn` funkcji, należy wybrać region z kontekstu urządzenia i użyć [CGDIObject::DeleteObject funkcji członkowskiej,](../../mfc/reference/cgdiobject-class.md#deleteobject) aby go usunąć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn::CRgn

Konstruuje `CRgn` obiekt.

```
CRgn();
```

### <a name="remarks"></a>Uwagi

Element `m_hObject` członkowski danych nie zawiera prawidłowego regionu GDI systemu Windows, `CRgn` dopóki obiekt nie zostanie zainicjowany przy jednej lub kilku innych funkcjach członkowskich.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateRoundRectRgn](#createroundrectrgn).

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::Equalrgn

Określa, czy dany region jest odpowiednikiem `CRgn` regionu przechowywanego w obiekcie.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parametry

*pRgn*<br/>
Identyfikuje region.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli oba regiony są równoważne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::OdRążej

Zwraca wskaźnik do `CRgn` obiektu po podaniu dojścia do regionu systemu Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parametry

*hRgn ( hRgn )*<br/>
Określa dojście do regionu systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRgn` obiektu. Jeśli funkcja nie powiodła się, zwracana wartość to NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CRgn` obiekt nie jest jeszcze dołączony do `CRgn` uchwytu, tworzony i dołączany jest obiekt tymczasowy. Ten `CRgn` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem mówienia jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn::GetRegionData

Wypełnia określony bufor danymi opisującymi region.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parametry

*lpRgnData*<br/>
Wskazuje strukturę danych [RGNDATA,](/windows/win32/api/wingdi/ns-wingdi-rgndata) która odbiera informacje. Jeśli ten parametr ma wartość NULL, zwracana wartość zawiera liczbę bajtów potrzebnych dla danych regionu.

*Ncount*<br/>
Określa rozmiar w bajtach buforu *lpRgnData.*

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się i *nCount* określa odpowiednią liczbę bajtów, zwracana wartość jest zawsze *nCount*. Jeśli funkcja nie powiedzie się lub *jeśli nCount* określa mniej niż odpowiednią liczbę bajtów, zwracana wartość wynosi 0 (błąd).

### <a name="remarks"></a>Uwagi

Dane te obejmują wymiary prostokątów, które tworzą region. Ta funkcja jest używana `CRgn::CreateFromData` w połączeniu z funkcją.

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

Pobiera współrzędne prostokąta obwiedni `CRgn` obiektu.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje na `RECT` strukturę lub `CRect` obiekt, aby otrzymać współrzędne prostokąta ograniczającego. Struktura `RECT` ma następującą formę:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Wartość zwracana

Określa typ regionu. Może to być dowolna z następujących wartości:

- COMPLEXREGION Region ma nakładające się obramowania.

- Region NULLREGION jest pusty.

- BŁĄD, `CRgn` obiekt nie określa prawidłowego regionu.

- REGION SIMPLEREGION nie ma nakładających się granic.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreatePolygonRgn](#createpolygonrgn).

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::OffsetRgn

Przenosi region przechowywany `CRgn` w obiekcie o określone przesunięcia.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Określa liczbę jednostek, które mają być przesuwne w lewo lub w prawo.

*Y*<br/>
Określa liczbę jednostek, które mają być przesuń w górę lub w dół.

*Punkt*<br/>
Współrzędna x *punktu* określa liczbę jednostek, które mają być przesuwne w lewo lub w prawo. Współrzędna y *punktu* określa liczbę jednostek do przesuń w górę lub w dół. Parametr *punktu* może być `POINT` strukturą `CPoint` lub obiektem.

### <a name="return-value"></a>Wartość zwracana

Typ nowego regionu. Może to być jedna z następujących wartości:

- COMPLEXREGION Region ma nakładające się obramowania.

- Uchwyt regionu BŁĄD jest nieprawidłowy.

- Region NULLREGION jest pusty.

- REGION SIMPLEREGION nie ma nakładających się granic.

### <a name="remarks"></a>Uwagi

Funkcja przesuwa jednostki regionu *x* wzdłuż osi x i *y* wzdłuż osi y.

Wartości współrzędnych regionu muszą być mniejsze lub równe 32 767 i większe lub równe -32 768. Parametry *x* i *y* muszą być starannie dobrane, aby zapobiec nieprawidłowym współrzędne regionu.

### <a name="example"></a>Przykład

  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::operator HRGN

Użyj tego operatora, aby uzyskać dołączony uchwyt `CRgn` GDI systemu Windows obiektu.

```
operator HRGN() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do obiektu `CRgn` GDI systemu Windows reprezentowanego przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewania, który obsługuje bezpośrednie korzystanie z obiektu HRGN.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz artykuł [Obiekty graficzne](/windows/win32/gdi/graphic-objects) w sdk systemu Windows.

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::PtRegion

Sprawdza, czy punkt podany przez *x* i *y* znajduje się w regionie przechowywanym `CRgn` w obiekcie.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parametry

*X*<br/>
Określa logiczną współrzędną x punktu do przetestowania.

*Y*<br/>
Określa logiczną współrzędną y punktu do przetestowania.

*Punkt*<br/>
Współrzędne *punktu* x- i y określają współrzędne x- i y punktu, aby przetestować wartość. Parametrem *punktu* może być `POINT` struktura `CPoint` lub obiekt.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli punkt znajduje się w regionie; w przeciwnym razie 0.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::RectInRegion

Określa, czy dowolna część prostokąta określona przez *lpRect* znajduje się `CRgn` w granicach regionu przechowywanego w obiekcie.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje na `RECT` strukturę lub `CRect` obiekt. Struktura `RECT` ma następującą formę:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli dowolna część określonego prostokąta znajduje się w granicach regionu; w przeciwnym razie 0.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::SetRectrgn

Tworzy prostokątny region.

```cpp
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Określa współrzędną x lewego górnego rogu prostokątnego regionu.

*y1*<br/>
Określa współrzędną y lewego górnego rogu prostokątnego regionu.

*x2*<br/>
Określa współrzędną x w prawym dolnym rogu prostokątnego regionu.

*y2*<br/>
Określa współrzędną y w prawym dolnym rogu prostokątnego regionu.

*Lprect*<br/>
Określa prostokątny obszar. Może być wskaźnikiem do `RECT` struktury `CRect` lub obiektu.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do [CreateRectRgn](#createrectrgn), jednak nie przydziela żadnej dodatkowej pamięci z lokalnej sterty aplikacji systemu Windows. Zamiast tego używa miejsca przydzielonego dla regionu `CRgn` przechowywanego w obiekcie. Oznacza to, `CRgn` że obiekt musi już zostać zainicjowany `SetRectRgn`z prawidłowym regionem systemu Windows przed wywołaniem . Punkty podane przez *x1*, *y1*, *x2*i *y2* określają minimalny rozmiar przydzielonego miejsca.

Użyj tej funkcji zamiast `CreateRectRgn` funkcji elementu członkowskiego, aby uniknąć wywołań do lokalnego menedżera pamięci.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
