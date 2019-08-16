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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503000"
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
|[CPalette:: CPalette](#cpalette)|Konstruuje `CPalette` obiekt bez dołączonej palety systemu Windows. Aby można było użyć `CPalette` obiektu, należy zainicjować go przy użyciu jednej z funkcji Członkowskich inicjujących.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette:: AnimatePalette](#animatepalette)|Zamienia wpisy w palecie logicznej identyfikowanej `CPalette` przez obiekt. Aplikacja nie musi aktualizować swojego obszaru klienckiego, ponieważ system Windows natychmiast mapuje nowe wpisy do palety systemowej.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Tworzy paletę półtonów dla kontekstu urządzenia i dołącza ją do `CPalette` obiektu.|
|[CPalette:: ispalette](#createpalette)|Tworzy paletę kolorów systemu Windows i dołącza ją do `CPalette` obiektu.|
|[CPalette::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPalette` obiektu, gdy ma dojść do obiektu palety systemu Windows.|
|[CPalette:: GetEntryCount](#getentrycount)|Pobiera liczbę wpisów palety w logicznej palecie.|
|[CPalette:: GetNearestPaletteIndex](#getnearestpaletteindex)|Zwraca indeks wpisu w logicznej palecie, który najlepiej pasuje do wartości koloru.|
|[CPalette:: GetPaletteEntries](#getpaletteentries)|Pobiera zakres wpisów z palety logicznej.|
|[CPalette:: ResizePalette](#resizepalette)|Zmienia rozmiar palety logicznej określonej przez `CPalette` obiekt na określoną liczbę wpisów.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Ustawia wartości i flagi koloru RGB w zakresie wpisów w palecie logicznej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette:: operator HPALETTE](#operator_hpalette)|Zwraca HPALETTE dołączony do `CPalette`.|

## <a name="remarks"></a>Uwagi

Paleta zapewnia interfejs między aplikacją a kolorowym urządzeniem wyjściowym (na przykład urządzeniem wyświetlającym). Interfejs umożliwia aplikacji pełne korzystanie z możliwości koloru urządzenia wyjściowego bez poważnego zakłócania kolorów wyświetlanych przez inne aplikacje. System Windows używa logicznej palety aplikacji (listy wymaganych kolorów) i palety systemowej (która definiuje dostępne kolory), aby określić używane kolory.

`CPalette` Obiekt zawiera funkcje członkowskie do manipulowania paletą, do której odwołuje się obiekt. Konstruowanie `CPalette` obiektu i używanie jego funkcji składowych do tworzenia rzeczywistej palety, obiektu interfejsu urządzenia graficznego (GDI) oraz do manipulowania jego wpisami i innymi właściwościami.

Aby uzyskać więcej informacji o `CPalette`używaniu programu, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="animatepalette"></a>CPalette:: AnimatePalette

Zamienia wpisy w palecie logicznej dołączone do `CPalette` obiektu.

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

Gdy aplikacja jest wywoływana `AnimatePalette`, nie musi aktualizować jej obszaru klienckiego, ponieważ system Windows natychmiast mapuje nowe wpisy do palety systemowej.

Funkcja będzie zmieniać tylko wpisy z flagą PC_RESERVED ustawioną w odpowiednim `palPaletteEntry` elemencie członkowskim struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , która jest dołączona do `CPalette` obiektu. `AnimatePalette` Aby uzyskać więcej informacji na temat tej struktury, zobacz LOGPALETTE w Windows SDK.

##  <a name="cpalette"></a>CPalette:: CPalette

Konstruuje `CPalette` obiekt.

```
CPalette();
```

### <a name="remarks"></a>Uwagi

Obiekt nie ma dołączonej palety, dopóki nie `CreatePalette` zostanie wywołana.

##  <a name="createhalftonepalette"></a>CPalette:: CreateHalftonePalette

Tworzy paletę półtonów dla kontekstu urządzenia.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identyfikuje kontekst urządzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja powinna utworzyć paletę półtonów, gdy tryb rozciągnięcia kontekstu urządzenia jest ustawiony na PÓŁTONy. Logiczna Paleta półtonów zwrócona przez funkcję elementu członkowskiego [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) powinna następnie zostać wybrana i zrealizowana w kontekście urządzenia przed wywołaniem funkcji [przechwytywania zmian:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) lub [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) .

Zobacz Windows SDK, aby uzyskać więcej informacji `CreateHalftonePalette` na `StretchDIBits`temat i.

##  <a name="createpalette"></a>CPalette:: ispalette

Inicjuje obiekt przez utworzenie logicznej palety kolorów systemu Windows i dołączenie jej `CPalette` do obiektu. `CPalette`

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Wskazuje strukturę [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , która zawiera informacje o kolorach w logicznej palecie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat `LOGPALETTE` struktury, zobacz Windows SDK.

##  <a name="fromhandle"></a>CPalette:: FromHandle

Zwraca wskaźnik do `CPalette` obiektu, gdy ma dojść do obiektu palety systemu Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Uchwyt palety kolorów interfejsu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPalette` obiektu, jeśli się powiedzie; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie jest jeszcze dołączony do palety systemu Windows, tworzony jest obiekt `CPalette` tymczasowy i jest on dołączony. `CPalette` Ten obiekt `CPalette` tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy, obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

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

Użyj tego operatora, aby uzyskać dojście `CPalette` do dołączonego interfejsu GDI systemu Windows.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows `CPalette` reprezentowane przez obiekt; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HPALETTE.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

##  <a name="resizepalette"></a>CPalette:: ResizePalette

Zmienia rozmiar palety logicznej dołączonej do `CPalette` obiektu do liczby wpisów określonych przez *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nNumEntries*<br/>
Określa liczbę wpisów w palecie po zmianie rozmiaru.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli rozmiar palety został pomyślnie zmieniony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja wywołuje `ResizePalette` w celu zmniejszenia rozmiaru palety, wpisy pozostałe w palecie o zmienionym rozmiarze nie są zmieniane. Jeśli aplikacja wywołuje `ResizePalette` w celu powiększania palety, dodatkowe wpisy palety są ustawiane na czerń (wartości czerwone, zielone i niebieskie są równe 0), a flagi dla wszystkich dodatkowych wpisów są ustawione na 0.

Aby uzyskać więcej informacji na temat interfejsu `ResizePalette`API systemu Windows, zobacz [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) w Windows SDK.

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

Jeśli w kontekście urządzenia podczas wywoływania `SetPaletteEntries`aplikacji jest zaznaczona paleta logiczna, zmiany zaczną obowiązywać dopiero po przełączeniu aplikacji do funkcji [przechwytywania:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Aby uzyskać więcej informacji, zobacz [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CPalette:: GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
