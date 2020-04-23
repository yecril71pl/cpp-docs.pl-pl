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
ms.openlocfilehash: f5740b3b073c4f564f9cac0fa04e5687ce1d8f00
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753675"
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
|[CPalette::CPalette](#cpalette)|Konstruuje `CPalette` obiekt bez dołączonej palety systemu Windows. Przed użyciem `CPalette` obiektu należy zainicjować obiekt przy użyciu jednej z funkcji elementu członkowskiego inicjowania.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Zastępuje wpisy w palecie logicznej `CPalette` identyfikowane przez obiekt. Aplikacja nie musi aktualizować swojego obszaru klienta, ponieważ system Windows natychmiast mapuje nowe wpisy do palety systemu.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Tworzy paletę półtonów dla kontekstu urządzenia i `CPalette` dołącza ją do obiektu.|
|[CPalette::CreatePalette](#createpalette)|Tworzy paletę kolorów systemu Windows i `CPalette` dołącza ją do obiektu.|
|[CPalette::OdHandle](#fromhandle)|Zwraca wskaźnik do `CPalette` obiektu po podaniu dojścia do obiektu palety systemu Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Pobiera liczbę wpisów palety w palecie logicznej.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Zwraca indeks wpisu w palecie logicznej, który najbardziej pasuje do wartości koloru.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Pobiera zakres wpisów palety w palecie logicznej.|
|[CPalette::ResizePalette](#resizepalette)|Zmienia rozmiar palety logicznej określonej przez `CPalette` obiekt na określoną liczbę wpisów.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Ustawia wartości kolorów rgb i flagi w zakresie wpisów w palecie logicznej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette::operator HPALETTE](#operator_hpalette)|Zwraca hpalette dołączone do `CPalette`.|

## <a name="remarks"></a>Uwagi

Paleta zapewnia interfejs między aplikacją a kolorowym urządzeniem wyjściowym (takim jak urządzenie wyświetlające). Interfejs pozwala aplikacji w pełni wykorzystać możliwości kolorów urządzenia wyjściowego bez poważnej ingerencji w kolory wyświetlane przez inne aplikacje. System Windows używa palety logicznej aplikacji (lista potrzebnych kolorów) i palety systemu (która definiuje dostępne kolory) w celu określenia użytych kolorów.

Obiekt `CPalette` udostępnia funkcje elementów członkowskich do manipulowania paletą, do której odnosi się obiekt. Konstruuj `CPalette` obiekt i użyj jego funkcji członkowskich, aby utworzyć rzeczywistą paletę, obiekt interfejsu urządzenia graficznego (GDI) oraz manipulować jego wpisami i innymi właściwościami.

Aby uzyskać więcej `CPalette`informacji na temat używania programu , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette::AnimatePalette

Zastępuje wpisy w palecie logicznej `CPalette` dołączonej do obiektu.

```cpp
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie, który ma być animowany.

*nNumEntries (Niemk.*<br/>
Określa liczbę wpisów w palecie, która ma być animowana.

*lpPaletteKolory*<br/>
Wskazuje pierwszy element członkowski tablicy struktur [PALETTEENTRY,](/previous-versions/dd162769\(v=vs.85\)) aby zastąpić wpisy palety identyfikowane przez *nStartIndex* i *nNumEntries*.

### <a name="remarks"></a>Uwagi

Gdy aplikacja `AnimatePalette`wywołuje , nie trzeba aktualizować swojego obszaru klienta, ponieważ system Windows mapuje nowe wpisy do palety systemu natychmiast.

Funkcja `AnimatePalette` zmieni tylko wpisy z flagą PC_RESERVED ustawioną `palPaletteEntry` w odpowiednim elementów członkowskich struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) dołączonej do `CPalette` obiektu. Więcej informacji na temat tej struktury można znaleźć w programie LOGPALETTE w programie Windows SDK.

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette

Konstruuje `CPalette` obiekt.

```
CPalette();
```

### <a name="remarks"></a>Uwagi

Obiekt nie ma dołączonej palety, dopóki nie zostanie wywołana, `CreatePalette` aby ją dołączyć.

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette

Tworzy paletę półtonów dla kontekstu urządzenia.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Identyfikuje kontekst urządzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja powinna utworzyć paletę półtonów, gdy tryb rozciągania kontekstu urządzenia jest ustawiony na HALFTONE. Następnie należy wybrać i zrealizować w kontekście urządzenia logiczną paletę półtonów zwróconą [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) przez funkcję elementu członkowskiego [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) [CreateHalftonePalette.](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette)

Zobacz SDK systemu Windows, `CreateHalftonePalette` `StretchDIBits`aby uzyskać więcej informacji na temat i .

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette

Inicjuje `CPalette` obiekt, tworząc logiczną paletę kolorów systemu `CPalette` Windows i dołączając ją do obiektu.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette (lpLogPalette)*<br/>
Wskazuje strukturę [LOGPALETTE,](/windows/win32/api/wingdi/ns-wingdi-logpalette) która zawiera informacje o kolorach w palecie logicznej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zobacz windows SDK, aby `LOGPALETTE` uzyskać więcej informacji na temat struktury.

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette::OdHandle

Zwraca wskaźnik do `CPalette` obiektu po podaniu dojścia do obiektu palety systemu Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette (paleta hpalette)*<br/>
Uchwyt do palety kolorów GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPalette` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CPalette` obiekt nie jest jeszcze dołączony do palety `CPalette` systemu Windows, tworzony i dołączany jest obiekt tymczasowy. Ten `CPalette` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę wpisów w danej palecie logicznej.

```
int GetEntryCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w palecie logicznej.

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex

Zwraca indeks wpisu w palecie logicznej, który najbardziej odpowiada określonej wartości koloru.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parametry

*CrColor ( kolor)*<br/>
Określa kolor, który ma być dopasowany.

### <a name="return-value"></a>Wartość zwracana

Indeks wpisu w palecie logicznej. Wpis zawiera kolor, który najbardziej prawie odpowiada określonej kolorystyce.

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries

Pobiera zakres wpisów palety w palecie logicznej.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie logicznej do pobrania.

*nNumEntries (Niemk.*<br/>
Określa liczbę wpisów w palecie logicznej do pobrania.

*lpPaletteKolory*<br/>
Wskazuje tablicę struktur danych [PALETTEENTRY,](/previous-versions/dd162769\(v=vs.85\)) aby odbierać wpisy palet. Tablica musi zawierać co najmniej tyle struktur danych, jak określono w *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów pobranych z palety logicznej; 0, jeśli funkcja nie powiodła się.

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::operator HPALETTE

Użyj tego operatora, aby uzyskać dołączony uchwyt `CPalette` GDI systemu Windows obiektu.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do obiektu `CPalette` GDI systemu Windows reprezentowanego przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewniczym, który obsługuje bezpośrednie wykorzystanie obiektu HPALETTE.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz artykuł [Obiekty graficzne](/windows/win32/gdi/graphic-objects) w sdk systemu Windows.

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::ResizePalette

Zmienia rozmiar palety logicznej dołączonej `CPalette` do obiektu na liczbę wpisów określoną przez *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nNumEntries (Niemk.*<br/>
Określa liczbę wpisów w palecie po jej ponownym zsaniu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli paleta została pomyślnie przesięta; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja `ResizePalette` wywołuje, aby zmniejszyć rozmiar palety, wpisy pozostałe w palecie o zmianie rozmiaru pozostają niezmienione. Jeśli aplikacja `ResizePalette` wywołuje powiększenie palety, dodatkowe wpisy palety są ustawione na czarny (czerwone, zielone i niebieskie wartości są wszystkie 0), a flagi dla wszystkich dodatkowych wpisów są ustawione na 0.

Aby uzyskać więcej informacji `ResizePalette`na temat interfejsu API systemu Windows, zobacz [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) w programie Windows SDK.

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries

Ustawia wartości kolorów rgb i flagi w zakresie wpisów w palecie logicznej.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palecie logicznej, który ma zostać ustawiony.

*nNumEntries (Niemk.*<br/>
Określa liczbę wpisów w palecie logicznej, która ma zostać ustawiona.

*lpPaletteKolory*<br/>
Wskazuje tablicę struktur danych [PALETTEENTRY,](/previous-versions/dd162769\(v=vs.85\)) aby odbierać wpisy palet. Tablica musi zawierać co najmniej tyle struktur danych, jak określono w *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów ustawionych w palecie logicznej; 0, jeśli funkcja nie powiodła się.

### <a name="remarks"></a>Uwagi

Jeśli paleta logiczna jest zaznaczona w `SetPaletteEntries`kontekście urządzenia podczas wywołania aplikacji, zmiany nie zostaną wprowadzone, dopóki aplikacja nie wywoła [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Aby uzyskać więcej informacji, zobacz [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykładowy DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
