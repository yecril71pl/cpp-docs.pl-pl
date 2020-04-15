---
title: Klasa CFont
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373844"
---
# <a name="cfont-class"></a>Klasa CFont

Hermetyzuje czcionkę interfejsu urządzenia graficznego systemu Windows (GDI) i udostępnia funkcje członkowskie do manipulowania czcionką.

## <a name="syntax"></a>Składnia

```
class CFont : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFont::CFont](#cfont)|Konstruuje `CFont` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicjuje `CFont` a z określonymi cechami.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicjuje `CFont` obiekt o właściwościach `LOGFONT` podanych w strukturze.|
|[CFont::CreatePointFont](#createpointfont)|Inicjuje `CFont` a o określonej wysokości, mierzona w dziesiątych części punktu i kroju pisma.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Tak `CreateFontIndirect` samo, jak z tą różnicą, że wysokość czcionki jest mierzona w dziesiątych częściach punktu, a nie w jednostkach logicznych.|
|[CFont::OdHandle](#fromhandle)|Zwraca wskaźnik do `CFont` obiektu, gdy podane systemu Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Wypełnia a `LOGFONT` informacjami o czcionce logicznej dołączonej `CFont` do obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|Zwraca uchwyt czcionki GDI systemu `CFont` Windows dołączony do obiektu.|

## <a name="remarks"></a>Uwagi

Aby użyć `CFont` obiektu, `CFont` należy skonstruować obiekt i dołączyć do niego czcionkę systemu Windows za pomocą [funkcji CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)lub [CreatePointFontIndirect](#createpointfontindirect), a następnie użyj funkcji elementów członkowskich obiektu do manipulowania czcionką.

`CreatePointFont` Funkcje `CreatePointFontIndirect` te są często łatwiejsze `CreateFont` `CreateFontIndirect` w użyciu niż lub od momentu automatycznego konwersji dla wysokości czcionki z rozmiaru punktu na jednostki logiczne.

Aby uzyskać `CFont`więcej informacji na temat , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont::CFont

Konstruuje `CFont` obiekt.

```
CFont();
```

### <a name="remarks"></a>Uwagi

Wynikowy obiekt musi zostać `CreateFont`zainicjowany `CreatePointFont`za `CreatePointFontIndirect` pomocą , `CreateFontIndirect`, lub przed jego użyciem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont

Inicjuje `CFont` obiekt o określonych właściwościach.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>Parametry

*nFeksja*<br/>
Określa żądaną wysokość (w jednostkach logicznych) czcionki. Opis `lfHeight` można znaleźć w strukturze [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)w zestaw windows SDK. Wartość bezwzględna *nHeight* nie może przekraczać 16 384 jednostek urządzenia po jego konwersji. Dla wszystkich porównań wysokości mapera czcionek szuka największej czcionki, która nie przekracza żądanego rozmiaru lub najmniejszej czcionki, jeśli wszystkie czcionki przekraczają żądany rozmiar.

*nWidth (ww.*<br/>
Określa średnią szerokość (w jednostkach logicznych) znaków czcionki. Jeśli *nWidth* wynosi 0, współczynnik proporcji urządzenia zostanie dopasowany do współczynnika proporcji digitalizacji dostępnych czcionek, aby znaleźć najbliższe dopasowanie, które jest określane przez wartość bezwzględną różnicy.

*nScapement (pejzaż)*<br/>
Określa kąt (w jednostkach 0,1 stopnia) między wektorem wychwytu a osią x powierzchni wyświetlacza. Wektor wychwytu jest linią przez początki pierwszego i ostatniego typu w wierszu. Kąt jest mierzony w kierunku przeciwnym do ruchu wskazówek zegara od osi x. Aby `lfEscapement` uzyskać więcej `LOGFONT` informacji, zobacz element członkowski w strukturze w programie Windows SDK.

*nOrientacja*<br/>
Określa kąt (w jednostkach 0,1 stopnia) między linią bazową znaku a osią x. Kąt jest mierzony w kierunku przeciwnym do ruchu wskazówek zegara od osi x dla układów współrzędnych, w których kierunek y jest w dół i zgodnie z ruchem wskazówek zegara od osi x dla układów współrzędnych, w których kierunek y jest w górę.

*n Waga*<br/>
Określa wagę czcionki (w pikselach odmówionych na 1000). Aby uzyskać więcej informacji, `LOGFONT` zobacz element członkowski *lfWeight* w strukturze w programie Windows SDK. Opisane wartości są przybliżone; rzeczywisty wygląd zależy od kroju pisma. Niektóre czcionki mają tylko FW_NORMAL, FW_REGULAR i FW_BOLD wagi. Jeśli określono FW_DONTCARE, używana jest waga domyślna.

*bWłaski*<br/>
Określa, czy czcionka jest kursywą.

*bPodkreślać*<br/>
Określa, czy czcionka jest podkreślona.

*cStrikeOut (Polski)*<br/>
Określa, czy znaki czcionki są wykreślane. Określa czcionkę przekreśloną, jeśli jest ustawiona na wartość niezerową.

*nCharSet (Zestaw chybianie)*<br/>
Określa zestaw znaków `lfCharSet` czcionkiZjej element członkowski w `LOGFONT` strukturze zestawu Windows SDK, aby uzyskać listę wartości.

Zestaw znaków OEM jest zależny od systemu.

Czcionki z innymi zestawami znaków mogą istnieć w systemie. Aplikacja, która używa czcionki z nieznanym zestawem znaków, nie może próbować tłumaczyć ani interpretować ciągów, które mają być renderowane za pomocą tej czcionki. Zamiast tego ciągi powinny być przekazywane bezpośrednio do sterownika urządzenia wyjściowego.

Maper czcionek nie używa wartości DEFAULT_CHARSET. Aplikacja może użyć tej wartości, aby umożliwić nazwę i rozmiar czcionki, aby w pełni opisać czcionkę logiczną. Jeśli czcionka o określonej nazwie nie istnieje, czcionkę z dowolnego zestawu znaków można zastąpić określoną czcionką. Aby uniknąć nieoczekiwanych wyników, aplikacje powinny używać wartości DEFAULT_CHARSET oszczędnie.

*nOutPrecision (OutPrecision)*<br/>
Określa żądaną dokładność wyjścia. Dokładność wyjściowa określa, jak ściśle dane wyjściowe muszą odpowiadać żądanej czcionce wysokość, szerokość, orientacja znaku, wychwyt i podział. Zobacz `lfOutPrecision` element członkowski w `LOGFONT` strukturze w zestawie Windows SDK, aby uzyskać listę wartości i więcej informacji.

*nClipPrecision (NClipPrecision)*<br/>
Określa żądaną dokładność przycinania. Dokładność przycinania definiuje sposób przycinania znaków, które są częściowo poza obszarem przycinania. Zobacz `lfClipPrecision` element członkowski w `LOGFONT` strukturze w zestawie Windows SDK, aby uzyskać listę wartości.

Aby użyć osadzonej czcionki tylko do odczytu, aplikacja musi określić CLIP_ENCAPSULATE.

Aby osiągnąć spójny obrót czcionek urządzenia, TrueType i wektorowych, aplikacja może użyć operatora OR do łączenia wartości CLIP_LH_ANGLES z dowolną z innych wartości *nClipPrecision.* Jeśli bit CLIP_LH_ANGLES jest ustawiony, obrót dla wszystkich czcionek zależy od tego, czy orientacja układu współrzędnych jest leworęczna czy praworęczna. (Aby uzyskać więcej informacji na temat orientacji układów współrzędnych, zobacz opis parametru *nOrientation).* Jeśli CLIP_LH_ANGLES nie jest ustawiona, czcionki urządzenia zawsze obracają się w kierunku przeciwnym do ruchu wskazówek zegara, ale obrót innych czcionek zależy od orientacji układu współrzędnych.

*nWzamienność*<br/>
Określa jakość wyjściową czcionki, która określa, jak dokładnie GDI musi próbować dopasować atrybuty czcionki logicznej do atrybutów rzeczywistej czcionki fizycznej. Zobacz `lfQuality` element członkowski w `LOGFONT` strukturze w zestawie Windows SDK, aby uzyskać listę wartości.

*nPitchAndRodzina*<br/>
Określa wysokość i rodzinę czcionki. Zobacz `lfPitchAndFamily` element członkowski w `LOGFONT` strukturze w zestawie Windows SDK, aby uzyskać listę wartości i więcej informacji.

*lpszNazeń*<br/>
A `CString` lub wskaźnik do ciągu zakończonego wartością null, który określa nazwę czcionki kroju pisma. Długość tego ciągu nie może przekraczać 30 znaków. Funkcja [EnumFontFamilies systemu](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) Windows może być używana do wyliczania wszystkich aktualnie dostępnych czcionek. Jeśli *lpszFacename* ma wartość NULL, GDI używa czcionki niezależnej od urządzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Czcionkę można następnie wybrać jako czcionkę dla dowolnego kontekstu urządzenia.

Funkcja `CreateFont` nie tworzy nowej czcionki GDI systemu Windows. Wybiera tylko najbliższe dopasowanie z fizycznych czcionek dostępnych dla GDI.

Aplikacje mogą używać ustawień domyślnych dla większości parametrów podczas tworzenia czcionki logicznej. Parametry, które powinny być zawsze podane konkretne wartości są *nHeight* i *lpszFacename*. Jeśli *nHeight* i *lpszFacename* nie są ustawiane przez aplikację, czcionka logiczna, która jest tworzona jest zależna od urządzenia.

Po `CFont` zakończeniu z obiektu utworzonego przez `CreateFont` funkcję, należy użyć, `CDC::SelectObject` aby wybrać `CFont` inną czcionkę w kontekście urządzenia, a następnie usunąć obiekt, który nie jest już potrzebny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::CreateFontIndirect

Inicjuje `CFont` obiekt o właściwościach podanych w strukturze [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Wskazuje strukturę definiują `LOGFONT` właściwości czcionki logicznej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Czcionkę można następnie wybrać jako bieżącą czcionkę dla dowolnego urządzenia.

Ta czcionka ma cechy określone w strukturze [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) Po wybraniu czcionki za pomocą funkcji elementu członkowskiego [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) maper czcionek GDI próbuje dopasować czcionkę logiczną do istniejącej czcionki fizycznej. Jeśli mapera czcionek nie może znaleźć dokładnego dopasowania dla czcionki logicznej, udostępnia alternatywną czcionkę, której cechy odpowiadają jak największej liczby żądanych cech.

Jeśli `CFont` nie potrzebujesz już obiektu `CreateFontIndirect` utworzonego `CDC::SelectObject` przez funkcję, użyj, aby wybrać inną `CFont` czcionkę w kontekście urządzenia, a następnie usuń obiekt, który nie jest już potrzebny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont

Ta funkcja umożliwia prosty sposób tworzenia czcionki o określonym kroju pisma i rozmiarze punktu.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*nPointSize (rozmiar)*<br/>
Żądana wysokość czcionki w dziesiątych częściach punktu. (Na przykład przekaż 120, aby zażądać czcionki 12-punktowej).

*lpszFaceName (Nazwa)*<br/>
A `CString` lub wskaźnik do ciągu zakończonego wartością null, który określa nazwę czcionki kroju pisma. Długość tego ciągu nie może przekraczać 30 znaków. Funkcja Windows 'EnumFontFamilies może być używana do wyliczenia wszystkich aktualnie dostępnych czcionek. Jeśli *lpszFaceName* ma wartość NULL, GDI używa czcionki niezależnej od urządzenia.

*Pdc*<br/>
Wskaźnik do obiektu [CDC,](../../mfc/reference/cdc-class.md) który ma być używany do konwersji wysokości w *nPointSize* na jednostki logiczne. Jeśli null, kontekst urządzenia ekranu jest używany do konwersji.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Automatycznie konwertuje wysokość w *nPointSize* do jednostek logicznych przy użyciu obiektu CDC wskazanego przez *pDC*.

Po zakończeniu z `CFont` obiektu utworzonego przez `CreatePointFont` funkcję, najpierw wybierz czcionkę z `CFont` kontekstu urządzenia, a następnie usuń obiekt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect

Ta funkcja jest taka sama jak [CreateFontIndirect,](#createfontindirect) z tą różnicą, `lfHeight` `LOGFONT` że element członkowski jest interpretowany w dziesiątych jednostek punktu, a nie urządzenia.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Wskazuje strukturę [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) która definiuje cechy czcionki logicznej. Element `lfHeight` członkowski `LOGFONT` struktury jest mierzony w dziesiątych częściach punktu, a nie w jednostkach logicznych. (Na przykład `lfHeight` ustawiona na 120, aby zażądać czcionki 12-punktowej).

*Pdc*<br/>
Wskaźnik do obiektu [CDC,](../../mfc/reference/cdc-class.md) który ma `lfHeight` być używany do konwersji wysokości na jednostki logiczne. Jeśli null, kontekst urządzenia ekranu jest używany do konwersji.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja automatycznie konwertuje `lfHeight` wysokość na jednostki logiczne przy użyciu obiektu `LOGFONT` CDC wskazywane przez *pDC* przed przekazaniem struktury do systemu Windows.

Po zakończeniu z `CFont` obiektu utworzonego przez `CreatePointFontIndirect` funkcję, najpierw wybierz czcionkę z `CFont` kontekstu urządzenia, a następnie usuń obiekt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont::OdHandle

Zwraca wskaźnik do `CFont` obiektu po podaniu uchwytu HFONT do obiektu czcionek GDI systemu Windows.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hFont ( hFont )*<br/>
Uchwyt HFONT do czcionki systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFont` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CFont` obiekt nie jest jeszcze dołączony do `CFont` uchwytu, tworzony i dołączany jest obiekt tymczasowy. Ten `CFont` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem mówienia jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont

Wywołanie tej funkcji, aby `LOGFONT` pobrać `CFont`kopię struktury dla .

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parametry

*pLogFont (pLogFont)*<br/>
Wskaźnik do struktury [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) aby otrzymać informacje o czcionce.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja powiedzie się, w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::operator HFONT

Użyj tego operatora, aby uzyskać uchwyt GDI systemu `CFont` Windows czcionki dołączonej do obiektu.

```
operator HFONT() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt obiektu czcionki GDI systemu `CFont` Windows dołączony do jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ponieważ ten operator jest automatycznie używany `CFont` do konwersji z [fontów i tekstu,](/windows/win32/gdi/fonts-and-text)można przekazać `CFont` obiekty do funkcji, które oczekują HFONTs.

Aby uzyskać więcej informacji na temat używania obiektów [graficznych,](/windows/win32/gdi/graphic-objects) zobacz Obiekty graficzne w sdk systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
