---
title: Klasa CPen
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364079"
---
# <a name="cpen-class"></a>Klasa CPen

Hermetyzuje pióro interfejsu urządzenia graficznego systemu Windows (GDI).

## <a name="syntax"></a>Składnia

```
class CPen : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPen::CPen](#cpen)|Konstruuje `CPen` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Tworzy logiczne pióro kosmetyczne lub geometryczne z określonymi atrybutami `CPen` stylu, szerokości i pędzla i dołącza je do obiektu.|
|[CPen::CreatePenIndirect](#createpenindirect)|Tworzy pióro ze stylem, szerokością i kolorem podanym w `CPen` strukturze [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) i dołącza je do obiektu.|
|[CPen::OdRą](#fromhandle)|Zwraca wskaźnik do `CPen` obiektu, gdy podano hpen systemu Windows.|
|[CPen::GetExtLogPen](#getextlogpen)|Pobiera [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) podstawowej struktury.|
|[CPen::GetLogPen](#getlogpen)|Pobiera [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) podstawowej struktury.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPen::operator HPEN](#operator_hpen)|Zwraca uchwyt systemu Windows `CPen` dołączony do obiektu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej `CPen`informacji na temat używania programu , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen::CPen

Konstruuje `CPen` obiekt.

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parametry

*Npenstyle*<br/>
Określa styl pióra. Ten parametr w pierwszej wersji konstruktora może być jedną z następujących wartości:

- PS_SOLID Tworzy pióro stałe.

- PS_DASH Tworzy pióro przerywane. Obowiązuje tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzenia.

- PS_DOT Tworzy pióro kropkowane. Obowiązuje tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzenia.

- PS_DASHDOT Tworzy pióro z naprzemiennymi myślnikami i kropkami. Obowiązuje tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzenia.

- PS_DASHDOTDOT Tworzy pióro z naprzemiennymi myślnikami i podwójnymi kropkami. Obowiązuje tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzenia.

- PS_NULL Tworzy pióro zerowe.

- PS_INSIDEFRAME Tworzy pióro, które rysuje linię wewnątrz ramki zamkniętych kształtów wytwarzanych przez funkcje wyjściowe GDI `Pie`systemu `Chord` Windows, które określają prostokąt ograniczający (na przykład `Ellipse`, `Rectangle`, `RoundRect`, i funkcje członkowskie). Jeśli ten styl jest używany z funkcjami wyjściowymi GDI systemu Windows, `LineTo` które nie określają prostokąta ograniczającego (na przykład funkcji elementu członkowskiego), obszar rysunku pióra nie jest ograniczony ramką.

Druga wersja `CPen` konstruktora określa kombinację atrybutów typu, stylu, zakończenia i sprzężenia. Wartości z każdej kategorii powinny być łączone przy użyciu bitowego operatora OR (&#124;). Typ pióra może być jedną z następujących wartości:

- PS_GEOMETRIC Tworzy pióro geometryczne.

- PS_COSMETIC Tworzy pióro kosmetyczne.

   Druga wersja konstruktora `CPen` dodaje następujące style pióra dla *nPenStyle:*

- PS_ALTERNATE Tworzy pióro, które ustawia co drugi piksel. (Ten styl ma zastosowanie tylko do długopisów kosmetycznych).

- PS_USERSTYLE Tworzy pióro, które używa tablicy stylizalizowania dostarczonej przez użytkownika.

   Zaślepka może być jedną z następujących wartości:

- PS_ENDCAP_ROUND Końcówki są okrągłe.

- PS_ENDCAP_SQUARE Zaślepki są kwadratowe.

- PS_ENDCAP_FLAT Zaślepki są płaskie.

   Sprzężenie może być jedną z następujących wartości:

- PS_JOIN_BEVEL Sprzężenia są skośne.

- PS_JOIN_MITER Sprzężenia są ścięte, gdy mieszczą się w bieżącym limicie ustawionym przez funkcję [SetMiterLimit.](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) Jeśli sprzężenie przekracza ten limit, jest skośne.

- PS_JOIN_ROUND Sprzężenia są okrągłe.

*nWidth (ww.*<br/>
Określa szerokość pióra.

- W przypadku pierwszej wersji konstruktora, jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia jest zawsze 1 piksel, niezależnie od trybu mapowania.

- Dla drugiej wersji konstruktora, if *nPenStyle* jest PS_GEOMETRIC, szerokość jest podana w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, szerokość musi być ustawiona na 1.

*CrColor ( kolor)*<br/>
Zawiera kolor RGB pióra.

*pLogBrush (pędzel)*<br/>
Wskazuje na `LOGBRUSH` strukturę. Jeśli *nPenStyle* jest PS_COSMETIC, *lbColor* element `LOGBRUSH` członkowski struktury określa kolor pióra i *lbStyle* element członkowski `LOGBRUSH` struktury musi być ustawiony na BS_SOLID. Jeśli *nPenStyle* jest PS_GEOMETRIC, wszystkie elementy członkowskie muszą być używane do określenia atrybutów pędzla pióra.

*nStyleCount (Liczba nStyleCount)*<br/>
Określa długość tablicy *lpStyle* w jednostkach dwusłownych. Ta wartość musi wynosić zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.

*styl lpStyle*<br/>
Wskazuje tablicę wartości dwusłownych. Pierwsza wartość określa długość pierwszej kreski w stylu zdefiniowanym przez użytkownika, druga wartość określa długość pierwszej spacji i tak dalej. Ten wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.

### <a name="remarks"></a>Uwagi

Jeśli konstruktora jest używany bez argumentów, `CPen` należy zainicjować wynikowy obiekt za pomocą funkcji `CreatePen`elementu członkowskiego , `CreatePenIndirect`lub . `CreateStockObject`

Jeśli używasz konstruktora, który przyjmuje argumenty, a następnie dalsze inicjowanie jest konieczne. Konstruktor z argumentami można zgłosić wyjątek, jeśli wystąpią błędy, podczas gdy konstruktor bez argumentów zawsze zakończy się pomyślnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::CreatePen

Tworzy logiczne pióro kosmetyczne lub geometryczne z określonymi atrybutami `CPen` stylu, szerokości i pędzla i dołącza je do obiektu.

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parametry

*Npenstyle*<br/>
Określa styl pióra. Aby uzyskać listę możliwych wartości, zobacz *parametr nPenStyle* w konstruktorze [CPen.](#cpen)

*nWidth (ww.*<br/>
Określa szerokość pióra.

- W przypadku pierwszej `CreatePen`wersji programu , jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia wynosi zawsze 1 piksel, niezależnie od trybu mapowania.

- W przypadku drugiej `CreatePen`wersji programu , if *nPenStyle* jest PS_GEOMETRIC, szerokość jest podana w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, szerokość musi być ustawiona na 1.

*CrColor ( kolor)*<br/>
Zawiera kolor RGB pióra.

*pLogBrush (pędzel)*<br/>
Wskazuje strukturę [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush) Jeśli *nPenStyle* jest PS_COSMETIC, `lbColor` element `LOGBRUSH` członkowski struktury określa kolor pióra i *lbStyle* element członkowski `LOGBRUSH` struktury musi być ustawiony na BS_SOLID. Jeśli nPenStyle jest PS_GEOMETRIC, wszystkie elementy członkowskie muszą być używane do określenia atrybutów pędzla pióra.

*nStyleCount (Liczba nStyleCount)*<br/>
Określa długość tablicy *lpStyle* w jednostkach dwusłownych. Ta wartość musi wynosić zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.

*styl lpStyle*<br/>
Wskazuje tablicę wartości dwusłownych. Pierwsza wartość określa długość pierwszej kreski w stylu zdefiniowanym przez użytkownika, druga wartość określa długość pierwszej spacji i tak dalej. Ten wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zakończy się pomyślnie lub zero, jeśli metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `CreatePen` inicjuje pióro o określonym stylu, szerokości i kolorze. Pióro można następnie wybrać jako bieżące pióro dla dowolnego kontekstu urządzenia.

Pióra o szerokości większej niż 1 piksel powinny zawsze mieć styl PS_NULL, PS_SOLID lub PS_INSIDEFRAME.

Jeśli pióro ma styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w tabeli kolorów logicznych, pióro jest rysowane z roztrząsanym kolorem. Styl pióra PS_SOLID nie może być użyty do utworzenia pióra z roztrząsanym kolorem. Styl PS_INSIDEFRAME jest identyczny z PS_SOLID, jeśli szerokość pióra jest mniejsza lub równa 1.

Druga wersja `CreatePen` inicjuje logiczne kosmetyczne lub geometryczne pióro, które ma określony styl, szerokość i atrybuty pędzla. Szerokość pióra kosmetycznego jest zawsze 1; szerokość pióra geometrycznego jest zawsze określona w jednostkach świata. Po aplikacji tworzy pióro logiczne, można wybrać, że pióro w kontekście urządzenia, wywołując [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcji. Po wybraniu pióra w kontekście urządzenia może ono służyć do rysowania linii i krzywych.

- Jeśli *nPenStyle* jest PS_COSMETIC i PS_USERSTYLE, wpisy w tablicy *lpStyle* określają długości kresek i spacji w jednostkach stylu. Jednostka stylu jest definiowana przez urządzenie, w którym pióro jest używane do rysowania linii.

- Jeśli *nPenStyle* jest PS_GEOMETRIC i PS_USERSTYLE, wpisy w tablicy *lpStyle* określają długości kresek i spacji w jednostkach logicznych.

- Jeśli *nPenStyle* jest PS_ALTERNATE, jednostka stylu jest ignorowana i ustawiany jest każdy inny piksel.

Gdy aplikacja nie wymaga już danego pióra, należy wywołać [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji elementu członkowskiego lub zniszczyć `CPen` obiekt, więc zasób nie jest już w użyciu. Aplikacja nie powinna usuwać pióra, gdy pióro jest zaznaczone w kontekście urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect

Inicjuje pióro, które ma styl, szerokość i kolor podane w strukturze wskazanej przez *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parametry

*lpLogPen*<br/>
Wskazuje strukturę [logpen](/windows/win32/api/Wingdi/ns-wingdi-logpen) systemu Windows, która zawiera informacje o piórze.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pióra o szerokości większej niż 1 piksel powinny zawsze mieć styl PS_NULL, PS_SOLID lub PS_INSIDEFRAME.

Jeśli pióro ma styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w tabeli kolorów logicznych, pióro jest rysowane z roztrząsanym kolorem. Styl PS_INSIDEFRAME jest identyczny z PS_SOLID, jeśli szerokość pióra jest mniejsza lub równa 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen::OdRą

Zwraca wskaźnik do `CPen` obiektu, do który dobiega uchwyt do obiektu pióra GDI systemu Windows.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parametry

*hPen*<br/>
`HPEN`do pióra GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPen` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CPen` obiekt nie jest dołączony do uchwytu, tworzony i dołączany jest obiekt tymczasowy. `CPen` Ten `CPen` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen::GetExtLogPen

Pobiera `EXTLOGPEN` podstawowej struktury.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Wskazuje strukturę [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) zawierającą informacje o piórze.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura `EXTLOGPEN` definiuje atrybuty stylu, szerokości i pędzla pióra. Na przykład `GetExtLogPen` wywołanie, aby dopasować do określonego stylu pióra.

Informacje na temat atrybutów pióra można znaleźć w następujących tematach w programie Windows SDK:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN ( EXTLOGPEN )](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [ODTWÓR Z REJESTRATORA](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [Odtwórz odtwórcz](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Przykład

W poniższym przykładzie `GetExtLogPen` kodu pokazano wywołanie, aby pobrać atrybuty pióra, a następnie utworzyć nowy, kosmetyczne pióro o tym samym kolorze.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen

Pobiera `LOGPEN` podstawowej struktury.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Wskazuje strukturę [LOGPEN,](/windows/win32/api/wingdi/ns-wingdi-logpen) aby zawierała informacje o piórze.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura `LOGPEN` definiuje styl, kolor i wzór pióra.

Na przykład `GetLogPen` wywołanie, aby dopasować do określonego stylu pióra.

Informacje na temat atrybutów pióra można znaleźć w następujących tematach w programie Windows SDK:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [ODTWÓR Z REJESTRATORA](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Przykład

W poniższym przykładzie `GetLogPen` kodu pokazano wywołanie, aby pobrać znak pióra, a następnie utworzyć nowe, stałe pióro o tym samym kolorze.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::operator HPEN

Pobiera dołączony uchwyt GDI systemu `CPen` Windows obiektu.

```
operator HPEN() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do obiektu `CPen` GDI systemu Windows reprezentowanego przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewniczym, który obsługuje bezpośrednie wykorzystanie obiektu HPEN.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz artykuł [Obiekty graficzne](/windows/win32/gdi/graphic-objects) w programie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBrush](../../mfc/reference/cbrush-class.md)
