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
ms.openlocfilehash: 952d270acd47b5834a06b731f7875ea2efdd4695
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502948"
---
# <a name="cpen-class"></a>Klasa CPen

Hermetyzuje pióro interfejsu urządzenia graficznego (GDI) systemu Windows.

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
|[CPen::CreatePen](#createpen)|Tworzy logiczne i geometryczne pióro, z określonym stylem, szerokością i pędzlem, a następnie dołącza je do `CPen` obiektu.|
|[CPen::CreatePenIndirect](#createpenindirect)|Tworzy pióro z stylem, szerokością i kolorem podanym w strukturze [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) i dołącza je do `CPen` obiektu.|
|[CPen::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPen` obiektu, w którym znajduje się HPEN systemu Windows.|
|[CPen::GetExtLogPen](#getextlogpen)|Pobiera podstawową strukturę [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) .|
|[CPen::GetLogPen](#getlogpen)|Pobiera podstawową strukturę [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPen:: operator HPEN](#operator_hpen)|Zwraca dojście systemu Windows dołączone do `CPen` obiektu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o `CPen`używaniu programu, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cpen"></a>CPen::CPen

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

*nPenStyle*<br/>
Określa styl pióra. Ten parametr w pierwszej wersji konstruktora może mieć jedną z następujących wartości:

- PS_SOLID tworzy pełne pióro.

- PS_DASH tworzy pióro kreskowane. Prawidłowy tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzeń.

- PS_DOT tworzy pióro kropkowane. Prawidłowy tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzeń.

- PS_DASHDOT tworzy pióro z przemiennymi kreskami i kropkami. Prawidłowy tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzeń.

- PS_DASHDOTDOT tworzy pióro z przemiennymi kreskami i kropkami. Prawidłowy tylko wtedy, gdy szerokość pióra wynosi 1 lub mniej, w jednostkach urządzeń.

- PS_NULL tworzy pióro o wartości null.

- PS_INSIDEFRAME tworzy pióro, które rysuje linię wewnątrz ramki kształtów zamkniętych utworzonych przez funkcje wyjściowe GDI systemu Windows, które określają prostokąt `Ellipse`ograniczający (na przykład `Rectangle` `RoundRect` `Pie`,,,, i `Chord`funkcje składowe). Gdy ten styl jest używany z funkcjami danych wyjściowych GDI systemu Windows, które nie określają ograniczenia prostokąta (na przykład `LineTo` funkcja członkowska), obszar rysowania pióra nie jest ograniczony przez ramkę.

Druga wersja `CPen` konstruktora określa kombinację atrybutów typu, stylu, zakończenia i sprzężenia. Wartości z każdej kategorii należy łączyć przy użyciu operatora bitowego or (&#124;). Typ pióra może mieć jedną z następujących wartości:

- PS_GEOMETRIC tworzy pióro geometryczne.

- PS_COSMETIC tworzy pióro kosmetyczne.

   Druga wersja `CPen` konstruktora dodaje następujące style pióra dla *nPenStyle*:

- PS_ALTERNATE tworzy pióro, które ustawia co drugi piksel. (Ten styl dotyczy tylko pisaków kosmetycznych).

- PS_USERSTYLE tworzy pióro, które używa tablicy stylów dostarczonej przez użytkownika.

   Zakończenie może być jedną z następujących wartości:

- PS_ENDCAP_ROUND zakończenia są okrągłe.

- PS_ENDCAP_SQUARE zakończenia są kwadratowe.

- PS_ENDCAP_FLAT zakończenia są płaskie.

   Sprzężenie może być jedną z następujących wartości:

- Sprzężenia PS_JOIN_BEVEL są fazowane.

- PS_JOIN_MITER Join są mitered, gdy znajdują się w bieżącym limicie ustawionym przez funkcję [SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) . Jeśli sprzężenie przekracza ten limit, zostanie on skośny.

- Sprzężenia PS_JOIN_ROUND są zaokrąglane.

*nWidth*<br/>
Określa szerokość pióra.

- W przypadku pierwszej wersji konstruktora, jeśli ta wartość jest równa 0, Szerokość w jednostkach urządzenia ma zawsze 1 piksel, niezależnie od trybu mapowania.

- W przypadku drugiej wersji konstruktora, jeśli *nPenStyle* jest PS_GEOMETRIC, Szerokość jest podawana w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, Szerokość musi być ustawiona na 1.

*crColor*<br/>
Zawiera kolor RGB dla pióra.

*pLogBrush*<br/>
`LOGBRUSH` Wskazuje strukturę. Jeśli *nPenStyle* jest PS_COSMETIC, `LOGBRUSH` element członkowski *lbColor* struktury określa kolor pióra, `LOGBRUSH` a element członkowski *lbStyle* musi być ustawiony na BS_SOLID. Jeśli *nPenStyle* jest PS_GEOMETRIC, wszystkie elementy członkowskie muszą być używane do określania atrybutów pędzla pióra.

*nStyleCount*<br/>
Określa długość w jednostkach DoubleWord tablicy *lpStyle* . Ta wartość musi być równa zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.

*lpStyle*<br/>
Wskazuje tablicę wartości DoubleWord. Pierwsza wartość określa długość pierwszej kreski w stylu zdefiniowanym przez użytkownika, drugą wartość określa długość pierwszego miejsca i tak dalej. Ten wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.

### <a name="remarks"></a>Uwagi

Jeśli używasz konstruktora bez argumentów, musisz zainicjować `CPen` otrzymany obiekt `CreatePen`za pomocą funkcji, `CreatePenIndirect`lub `CreateStockObject` .

Jeśli używasz konstruktora, który przyjmuje argumenty, to dalsze inicjowanie nie jest konieczne. Konstruktor z argumentami może zgłosić wyjątek w przypadku napotkania błędów, podczas gdy Konstruktor bez argumentów zawsze zakończy się powodzeniem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>CPen::CreatePen

Tworzy logiczne i geometryczne pióro, z określonym stylem, szerokością i pędzlem, a następnie dołącza je do `CPen` obiektu.

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

*nPenStyle*<br/>
Określa styl pióra. Aby uzyskać listę możliwych wartości, zobacz parametr *nPenStyle* w konstruktorze [CPen](#cpen) .

*nWidth*<br/>
Określa szerokość pióra.

- W przypadku pierwszej wersji `CreatePen`, jeśli wartość jest równa 0, Szerokość w jednostkach urządzenia jest zawsze 1 piksel, niezależnie od trybu mapowania.

- W przypadku drugiej wersji programu `CreatePen`, jeśli *nPenStyle* jest PS_GEOMETRIC, Szerokość jest podawana w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, Szerokość musi być ustawiona na 1.

*crColor*<br/>
Zawiera kolor RGB dla pióra.

*pLogBrush*<br/>
Wskazuje na strukturę [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) . Jeśli *nPenStyle* jest PS_COSMETIC `lbColor` , element `LOGBRUSH` członkowski struktury określa kolor `LOGBRUSH` pióra, a element członkowski *lbStyle* struktury musi być ustawiony na BS_SOLID. Jeśli nPenStyle jest PS_GEOMETRIC, wszystkie elementy członkowskie muszą być używane do określania atrybutów pędzla pióra.

*nStyleCount*<br/>
Określa długość w jednostkach DoubleWord tablicy *lpStyle* . Ta wartość musi być równa zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.

*lpStyle*<br/>
Wskazuje tablicę wartości DoubleWord. Pierwsza wartość określa długość pierwszej kreski w stylu zdefiniowanym przez użytkownika, drugą wartość określa długość pierwszego miejsca i tak dalej. Ten wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli kończy się pomyślnie, lub zero, jeśli metoda się nie powiedzie.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `CreatePen` inicjuje pióro z określonym stylem, szerokością i kolorem. Pióro można następnie wybrać jako bieżące pióro dla dowolnego kontekstu urządzenia.

Pióra o szerokości większej niż 1 piksel powinna zawsze mieć styl PS_NULL, PS_SOLID lub PS_INSIDEFRAME.

Jeśli pióro ma styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w logicznej tabeli kolorów, pióro jest rysowane kolorem. Nie można użyć stylu pióra PS_SOLID, aby utworzyć pióro z kolorem. Styl PS_INSIDEFRAME jest identyczny z PS_SOLID, jeśli szerokość pióra jest mniejsza lub równa 1.

Druga wersja `CreatePen` inicjująca logiczne lub geometryczne pióro, które ma określony styl, Szerokość i atrybuty pędzla. Szerokość pióra kosmetycznego jest zawsze 1. Szerokość pióra geometrycznego jest zawsze określona w jednostkach świata. Po utworzeniu przez aplikację piórem logicznym można wybrać ten pióro w kontekście urządzenia, wywołując funkcję przepustek [:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) . Po wybraniu pióra w kontekście urządzenia może służyć do rysowania linii i krzywych.

- Jeśli *nPenStyle* jest PS_COSMETIC i PS_USERSTYLE, wpisy w tablicy *lpStyle* określają długości kresek i spacji w jednostkach stylu. Jednostka stylu jest definiowana przez urządzenie, w którym pióro jest używane do rysowania linii.

- Jeśli *nPenStyle* jest PS_GEOMETRIC i PS_USERSTYLE, wpisy w tablicy *lpStyle* określają długości kresek i spacji w jednostkach logicznych.

- Jeśli *nPenStyle* jest PS_ALTERNATE, jednostka stylu jest ignorowana, a każdy inny piksel jest ustawiony.

Gdy aplikacja nie wymaga już danego pióra, powinien wywołać funkcję członkowską [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) lub zniszczyć `CPen` obiekt, aby zasób nie był już używany. Aplikacja nie powinna usuwać pióra, gdy pióro jest zaznaczone w kontekście urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>CPen::CreatePenIndirect

Inicjuje pióro z stylem, szerokością i kolorem podanym w strukturze wskazywanym przez *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parametry

*lpLogPen*<br/>
Wskazuje strukturę [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) systemu Windows, która zawiera informacje o piórie.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pióra o szerokości większej niż 1 piksel powinna zawsze mieć styl PS_NULL, PS_SOLID lub PS_INSIDEFRAME.

Jeśli pióro ma styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w logicznej tabeli kolorów, pióro jest rysowane kolorem. Styl PS_INSIDEFRAME jest identyczny z PS_SOLID, jeśli szerokość pióra jest mniejsza lub równa 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>CPen::FromHandle

Zwraca wskaźnik do `CPen` obiektu, który ma uchwyt do obiektu pióra GDI systemu Windows.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parametry

*hPen*<br/>
`HPEN`uchwyt do pióra GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPen` obiektu, jeśli się powiedzie; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie jest dołączony do dojścia, tworzony jest obiekt `CPen` tymczasowy i jest on dołączony. `CPen` Ten obiekt `CPen` tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy, obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>CPen::GetExtLogPen

`EXTLOGPEN` Pobiera podstawową strukturę.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Wskazuje strukturę [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) , która zawiera informacje o piórie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`EXTLOGPEN` Struktura definiuje styl, Szerokość i atrybuty pędzla pióra. Na przykład, wywołaj `GetExtLogPen` , aby dopasować określony styl pióra.

Zapoznaj się z następującymi tematami w Windows SDK, aby uzyskać informacje o atrybutach pióra:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje wywołanie `GetExtLogPen` , aby pobrać atrybuty pióra, a następnie utworzyć nowe, kosmetyczne pióro z tym samym kolorem.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>CPen::GetLogPen

`LOGPEN` Pobiera podstawową strukturę.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Wskazuje strukturę [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) , aby zawierała informacje o piórie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`LOGPEN` Struktura definiuje styl, kolor i deseń pióra.

Na przykład, wywołaj `GetLogPen` , aby dopasować określony styl pióra.

Zapoznaj się z następującymi tematami w Windows SDK, aby uzyskać informacje o atrybutach pióra:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje wywołanie `GetLogPen` w celu pobrania znaku pióra, a następnie utworzenie nowego, pełnego pióra z tym samym kolorem.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>CPen:: operator HPEN

Pobiera dołączone dojście `CPen` GDI systemu Windows obiektu.

```
operator HPEN() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows `CPen` reprezentowane przez obiekt; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HPEN.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz artykuł [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBrush](../../mfc/reference/cbrush-class.md)
