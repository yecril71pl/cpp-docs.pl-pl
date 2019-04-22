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
ms.openlocfilehash: f0105a8ee33a57f7431a9c6a97b4b132f291f42a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770818"
---
# <a name="cpalette-class"></a>Klasa CPalette

Hermetyzuje palety kolorów Windows.

## <a name="syntax"></a>Składnia

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Konstruuje `CPalette` obiektu, nie dołączonych palety Windows. Należy zainicjować `CPalette` obiektu przy użyciu jednego z inicjowanie funkcji Członkowskich, zanim będzie można jej używać.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Zastępuje wpisy palety logiczne identyfikowane przez `CPalette` obiektu. Aplikacja nie ma można zaktualizować obszaru klienckiego, ponieważ Windows mapuje nowych wpisów na palecie system natychmiast.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Paleta półtonów kontekstu urządzenia i dołącza je do `CPalette` obiektu.|
|[CPalette::CreatePalette](#createpalette)|Tworzy palety kolorów Windows i dołącza je do `CPalette` obiektu.|
|[CPalette::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPalette` obiektu, gdy dojścia do obiektu Windows palety.|
|[CPalette::GetEntryCount](#getentrycount)|Pobiera numer wpisy palety logiczne palety.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Zwraca indeks wpis logiczną paletę, która najlepiej pasuje do wartości koloru.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Pobiera zakres wpisy palety logiczne palety.|
|[CPalette::ResizePalette](#resizepalette)|Zmienia rozmiar logiczną paletę określony przez `CPalette` obiektu określoną liczbę pozycji.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Ustawia wartości kolorów RGB i flagi w zakresie wpisy palety logiczne.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[HPALETTE CPalette::operator](#operator_hpalette)|Zwraca HPALETTE dołączone do `CPalette`.|

## <a name="remarks"></a>Uwagi

Palety udostępnia interfejs między aplikacją a urządzeniem kolor danych wyjściowych (np. urządzenia wyświetlającego). Interfejs umożliwia aplikacji, w pełni wykorzystać możliwości kolor urządzenia wyjściowego bez konieczności zmieniania poważnie kolory wyświetlane przez inne aplikacje. Windows korzysta z palety logiczne aplikacji (Lista kolorów wymagane) i paleta systemu, (która określa dostępnych kolorów), aby określić kolory używane.

Element `CPalette` obiektu dostarcza funkcji elementów członkowskich do manipulowania palety określonego przez obiekt. Konstruowania `CPalette` obiektu i używać jej elementów członkowskich, do tworzenia rzeczywistych palety, obiekt interface (GDI) urządzenia grafiki i operowania nim wpisów oraz inne właściwości.

Aby uzyskać więcej informacji na temat korzystania z `CPalette`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="animatepalette"></a>  CPalette::AnimatePalette

Zastępuje wpisy palety logiczne, dołączone do `CPalette` obiektu.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w palety aby być animowane.

*nNumEntries*<br/>
Określa liczbę wpisów w palety aby być animowane.

*lpPaletteColors*<br/>
Wskazuje pierwszego elementu członkowskiego tablicy [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) struktur, aby zastąpić wpisy palety identyfikowane przez *nStartIndex* i *nNumEntries*.

### <a name="remarks"></a>Uwagi

Kiedy aplikacja wywołuje `AnimatePalette`, nie ma aktualizacji obszaru klienckiego, ponieważ Windows mapuje nowych wpisów na palecie system natychmiast.

`AnimatePalette` Funkcji spowoduje jedynie zmianę wpisów z flagą PC_RESERVED w odpowiednich `palPaletteEntry` członkiem [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) strukturę, która jest dołączona do `CPalette` obiektu. Zobacz LOGPALETTE w zestawie Windows SDK, aby uzyskać więcej informacji na temat tej struktury.

##  <a name="cpalette"></a>  CPalette::CPalette

Konstruuje `CPalette` obiektu.

```
CPalette();
```

### <a name="remarks"></a>Uwagi

Obiekt ma nie dołączonych palety, dopóki nie zostanie wywołana `CreatePalette` można dołączyć jeden.

##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette

Tworzy palety półtonów kontekstu urządzenia.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identyfikuje kontekst urządzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikację należy utworzyć palety półtonów, gdy PÓŁTONÓW ma wartość trybu rozciągania kontekstu urządzenia. Palety logiczne półtonów zwrócony przez [CreateHalftonePalette](/windows/desktop/api/wingdi/nf-wingdi-createhalftonepalette) funkcja elementu członkowskiego należy następnie można wybrać i wykonywane w kontekście urządzenia przed [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) lub [ StretchDIBits](/windows/desktop/api/wingdi/nf-wingdi-stretchdibits) funkcja jest wywoływana.

Zobacz zestaw SDK Windows, aby uzyskać więcej informacji na temat `CreateHalftonePalette` i `StretchDIBits`.

##  <a name="createpalette"></a>  CPalette::CreatePalette

Inicjuje `CPalette` obiektu, tworząc Windows logiczną paletę i dołączania ich do `CPalette` obiektu.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Wskazuje [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) strukturę, która zawiera informacje dotyczące kolorów palety logiczne.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zobacz zestaw SDK Windows, aby uzyskać więcej informacji na temat `LOGPALETTE` struktury.

##  <a name="fromhandle"></a>  CPalette::FromHandle

Zwraca wskaźnik do `CPalette` obiektu, gdy dojścia do obiektu Windows palety.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Dojście do palety kolorów Windows GDI.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPalette` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CPalette` obiekt nie jest już dołączony do palety Windows, tymczasowego `CPalette` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CPalette` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, w której czas wszystkich tymczasowych grafiki obiekty zostaną usunięte. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jednego okna.

##  <a name="getentrycount"></a>  CPalette::GetEntryCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę wpisów w danym palety logiczne.

```
int GetEntryCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w palety logiczne.

##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex

Zwraca indeks wpisu w palecie logiczny, który najlepiej pasuje do wartości określonego koloru.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Określa kolor do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Indeks wpis palety logiczne. Wpis zawiera kolor, który najlepiej pasuje określonego koloru.

##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries

Pobiera zakres wpisy palety logiczne palety.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w logiczną paletę do pobrania.

*nNumEntries*<br/>
Określa liczbę wpisów w logiczną paletę do pobrania.

*lpPaletteColors*<br/>
Wskazuje na tablicę [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) struktur danych, aby otrzymać wpisy palety. Tablica musi zawierać co najmniej tyle struktur danych określony przez *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów jest pobierana z logiczną paletę; 0, jeśli funkcja nie powiodło się.

##  <a name="operator_hpalette"></a>  HPALETTE CPalette::operator

Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CPalette` obiektu.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, dojścia do obiektu Windows GDI reprezentowany przez `CPalette` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia obiektu HPALETTE.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

##  <a name="resizepalette"></a>  CPalette::ResizePalette

Zmienia rozmiar logiczną paletę dołączone do `CPalette` obiektu do liczby pozycji określonej przez *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nNumEntries*<br/>
Określa liczbę wpisów w palecie po został zmieniony.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli palety został pomyślnie zmieniony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja wywołuje `ResizePalette` pozwala zmniejszyć paletę pozostałe w palecie o zmienionym rozmiarze wpisy ulegną zmianie. Jeśli aplikacja wywołuje `ResizePalette` Aby powiększyć palety, wpisy palety dodatkowe są ustawione na czarny (wartość czerwonego, zielonego i niebieskiego są wszystkie 0), a flagi dla wszystkich wpisów dodatkowe są ustawione na 0.

Aby uzyskać więcej informacji na temat interfejsu API Windows `ResizePalette`, zobacz [ResizePalette](/windows/desktop/api/wingdi/nf-wingdi-resizepalette) w zestawie Windows SDK.

##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries

Ustawia wartości kolorów RGB i flagi w zakresie wpisy palety logiczne.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Określa pierwszy wpis w logiczną paletę do ustawienia.

*nNumEntries*<br/>
Określa liczbę wpisów w logiczną paletę do ustawienia.

*lpPaletteColors*<br/>
Wskazuje na tablicę [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) struktur danych, aby otrzymać wpisy palety. Tablica musi zawierać co najmniej tyle struktur danych określony przez *nNumEntries*.

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w logiczną paletę; 0, jeśli funkcja nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli logiczną paletę zostanie wybrany do kontekstu urządzenia, gdy aplikacja wywołuje `SetPaletteEntries`, zmiany nie zostały zastosowane do czasu wywołania aplikacji [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Aby uzyskać więcej informacji na temat struktury Windows `PALETTEENTRY`, zobacz [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Próbki MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
