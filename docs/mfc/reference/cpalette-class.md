---
title: Klasa CPalette
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855535"
---
# <a name="cpalette-class"></a>Klasa CPalette

Hermetyzuje paletę kolorów systemu Windows.

## <a name="syntax"></a>Składnia

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette:: CPalette](#cpalette)|Konstruuje obiekt `CPalette` bez dołączonej palety systemu Windows. Aby można było użyć obiektu `CPalette`, należy zainicjować go przy użyciu jednej z funkcji Członkowskich inicjujących.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette:: AnimatePalette](#animatepalette)|Zamienia wpisy w palecie logicznej identyfikowane przez obiekt `CPalette`. Aplikacja nie musi aktualizować swojego obszaru klienckiego, ponieważ system Windows natychmiast mapuje nowe wpisy do palety systemowej.|
|[CPalette:: CreateHalftonePalette](#createhalftonepalette)|Tworzy paletę półtonów dla kontekstu urządzenia i dołącza ją do obiektu `CPalette`.|
|[CPalette:: ispalette](#createpalette)|Tworzy paletę kolorów systemu Windows i dołącza ją do obiektu `CPalette`.|
|[CPalette:: FromHandle](#fromhandle)|Zwraca wskaźnik do obiektu `CPalette`, gdy ma dojść do obiektu palety systemu Windows.|
|[CPalette:: GetEntryCount](#getentrycount)|Pobiera liczbę wpisów palety w logicznej palecie.|
|[CPalette:: GetNearestPaletteIndex](#getnearestpaletteindex)|Zwraca indeks wpisu w logicznej palecie, który najlepiej pasuje do wartości koloru.|
|[CPalette:: GetPaletteEntries](#getpaletteentries)|Pobiera zakres wpisów z palety logicznej.|
|[CPalette:: ResizePalette](#resizepalette)|Zmienia rozmiar palety logicznej określonej przez obiekt `CPalette` na określoną liczbę wpisów.|
|[CPalette:: SetPaletteEntries](#setpaletteentries)|Ustawia wartości i flagi koloru RGB w zakresie wpisów w palecie logicznej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette:: operator HPALETTE](#operator_hpalette)|Zwraca HPALETTE dołączony do `CPalette`.|

## <a name="remarks"></a>Uwagi

Paleta zapewnia interfejs między aplikacją a kolorowym urządzeniem wyjściowym (na przykład urządzeniem wyświetlającym). Interfejs umożliwia aplikacji pełne korzystanie z możliwości koloru urządzenia wyjściowego bez poważnego zakłócania kolorów wyświetlanych przez inne aplikacje. System Windows używa logicznej palety aplikacji (listy wymaganych kolorów) i palety systemowej (która definiuje dostępne kolory), aby określić używane kolory.

Obiekt `CPalette` udostępnia funkcje członkowskie do manipulowania paletą, do której odwołuje się obiekt. Konstruowanie obiektu `CPalette` i używanie jego funkcji składowych do tworzenia rzeczywistej palety, obiektu interfejsu urządzenia graficznego (GDI) oraz do manipulowania jego wpisami i innymi właściwościami.

Aby uzyskać więcej informacji na temat używania `CPalette`, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="animatepalette"></a>CPalette:: AnimatePalette

Zamienia wpisy w palecie logicznej dołączone do obiektu `CPalette`.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie, który ma być animowany.

*nNumEntries*<br/>
Określa liczbę wpisów w palecie, które mają być animowane.

*lpPaletteColors*<br/>
Wskazuje pierwszy element członkowski tablicy struktur [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) , aby zastąpić wpisy palety identyfikowane przez *nStartIndex* i *nNumEntries*.

### <a name="remarks"></a>Uwagi

Gdy aplikacja wywołuje `AnimatePalette`, nie musi aktualizować jej obszaru klienckiego, ponieważ system Windows natychmiast mapuje nowe wpisy do palety systemowej.

Funkcja `AnimatePalette` będzie zmieniać tylko wpisy z flagą PC_RESERVED ustawioną w odpowiednim `palPaletteEntry` elemencie członkowskim struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , która jest dołączona do obiektu `CPalette`. Aby uzyskać więcej informacji na temat tej struktury, zobacz LOGPALETTE w Windows SDK.

##  <a name="cpalette"></a>CPalette:: CPalette

Konstruuje obiekt `CPalette`.

```
CPalette();
```

### <a name="remarks"></a>Uwagi

Obiekt nie ma dołączonej palety do momentu wywołania `CreatePalette`, aby je dołączyć.

##  <a name="createhalftonepalette"></a>CPalette:: CreateHalftonePalette

Tworzy paletę półtonów dla kontekstu urządzenia.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Identyfikuje kontekst urządzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja powinna utworzyć paletę półtonów, gdy tryb rozciągnięcia kontekstu urządzenia jest ustawiony na PÓŁTONy. Logiczna Paleta półtonów zwrócona przez funkcję elementu członkowskiego [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) powinna następnie zostać wybrana i zrealizowana w kontekście urządzenia przed wywołaniem funkcji [przechwytywania zmian:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) lub [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) .

Więcej informacji na temat `CreateHalftonePalette` i `StretchDIBits`znajduje się w Windows SDK.

##  <a name="createpalette"></a>CPalette:: ispalette

Inicjuje obiekt `CPalette` przez utworzenie logicznej palety kolorów systemu Windows i dołączenie jej do obiektu `CPalette`.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Wskazuje strukturę [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , która zawiera informacje o kolorach w logicznej palecie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat struktury `LOGPALETTE`, zobacz Windows SDK.

##  <a name="fromhandle"></a>CPalette:: FromHandle

Zwraca wskaźnik do obiektu `CPalette`, gdy ma dojść do obiektu palety systemu Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Uchwyt palety kolorów interfejsu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CPalette`, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli obiekt `CPalette` nie jest już dołączony do palety systemu Windows, zostanie utworzony i dołączony tymczasowy obiekt `CPalette`. Ten tymczasowy `CPalette` obiektu jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy, obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

##  <a name="getentrycount"></a>CPalette:: GetEntryCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę wpisów w danej palecie logicznej.

```
int GetEntryCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w logicznej palecie.

##  <a name="getnearestpaletteindex"></a>CPalette:: GetNearestPaletteIndex

Zwraca indeks wpisu w logicznej palecie, który najlepiej pasuje do określonej wartości koloru.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Określa kolor, który ma zostać dopasowany.

### <a name="return-value"></a>Wartość zwracana

Indeks wpisu w logicznej palecie. Wpis zawiera kolor, który jest najbardziej zbliżony do określonego koloru.

##  <a name="getpaletteentries"></a>CPalette:: GetPaletteEntries

Pobiera zakres wpisów z palety logicznej.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie logicznej, który ma zostać pobrany.

*nNumEntries*<br/>
Określa liczbę wpisów w palecie logicznej do pobrania.

*lpPaletteColors*<br/>
Wskazuje tablicę struktur danych [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) do odbierania wpisów palety. Tablica musi zawierać co najmniej tyle struktur danych jak określono przez *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów pobranych z palety logicznej; 0, jeśli funkcja nie powiodła się.

##  <a name="operator_hpalette"></a>CPalette:: operator HPALETTE

Użyj tego operatora, aby uzyskać dojście do dołączonego interfejsu GDI systemu Windows obiektu `CPalette`.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows reprezentowanego przez obiekt `CPalette`; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HPALETTE.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

##  <a name="resizepalette"></a>CPalette:: ResizePalette

Zmienia rozmiar palety logicznej dołączonej do obiektu `CPalette` do liczby wpisów określonych przez *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nNumEntries*<br/>
Określa liczbę wpisów w palecie po zmianie rozmiaru.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli rozmiar palety został pomyślnie zmieniony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja wywoła `ResizePalette` w celu zmniejszenia rozmiaru palety, wpisy pozostałe w palecie o zmienionym rozmiarze nie są zmieniane. Jeśli aplikacja wywoła `ResizePalette` w celu powiększania palety, dodatkowe wpisy palety są ustawiane na czerń (czerwone, zielone i niebieskie wartości są równe 0), a flagi dla wszystkich dodatkowych wpisów są ustawione na 0.

Aby uzyskać więcej informacji na `ResizePalette`Windows API, zobacz [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) in the Windows SDK.

##  <a name="setpaletteentries"></a>CPalette:: SetPaletteEntries

Ustawia wartości i flagi koloru RGB w zakresie wpisów w palecie logicznej.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie logicznej, który ma zostać ustawiony.

*nNumEntries*<br/>
Określa liczbę wpisów w palecie logicznej, która ma zostać ustawiona.

*lpPaletteColors*<br/>
Wskazuje tablicę struktur danych [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) do odbierania wpisów palety. Tablica musi zawierać co najmniej tyle struktur danych jak określono przez *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów ustawionych w palecie logicznej; 0, jeśli funkcja nie powiodła się.

### <a name="remarks"></a>Uwagi

Jeśli w kontekście urządzenia zostanie wybrana paleta logiczna, gdy aplikacja wywoła `SetPaletteEntries`, zmiany zaczną obowiązywać do momentu wywołania aplikacji do funkcji [przechwytywania:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Aby uzyskać więcej informacji, zobacz [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CPalette:: GetPaletteEntries](#getpaletteentries)<br/>
[CPalette:: SetPaletteEntries](#setpaletteentries)
