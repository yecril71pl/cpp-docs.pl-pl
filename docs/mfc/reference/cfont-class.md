---
title: Klasa CFont | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 760f8c5527f0dbd4fa0ebc2aed3aed59a9676b82
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399025"
---
# <a name="cfont-class"></a>Klasa CFont

Hermetyzuje czcionkę Windows graphics urządzenia interface (GDI) i dostarcza funkcji elementów członkowskich do manipulowania czcionką.

## <a name="syntax"></a>Składnia

```
class CFont : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFont::CFont](#cfont)|Konstruuje `CFont` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicjuje `CFont` o określonej charakterystyce.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicjuje `CFont` obiekt z właściwościami w `LOGFONT` struktury.|
|[CFont::CreatePointFont](#createpointfont)|Inicjuje `CFont` o określonej wysokości, mierzony w liczbę dziesiątych części punktu i krój czcionki.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Taki sam jak `CreateFontIndirect` z tą różnicą, że wysokość czcionki jest mierzony w liczbę dziesiątych części punkt, a nie jednostki logiczne.|
|[CFont::FromHandle](#fromhandle)|Zwraca wskaźnik do `CFont` obiektu, gdy Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Wypełnia `LOGFONT` informacji o logicznych czcionki, dołączone do `CFont` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[HFONT CFont::operator](#operator_hfont)|Zwraca uchwyt czcionki Windows GDI dołączonych do `CFont` obiektu.|

## <a name="remarks"></a>Uwagi

Do użycia `CFont` obiektów, konstruowania `CFont` obiektu i dołączyć czcionkę Windows do niego za pomocą [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), lub [CreatePointFontIndirect](#createpointfontindirect), a następnie użyj funkcji elementów członkowskich obiektu do manipulowania czcionki.

`CreatePointFont` i `CreatePointFontIndirect` funkcje są często łatwiejsze w użyciu niż `CreateFont` lub `CreateFontIndirect` ponieważ robią konwersji wysokość czcionki od rozmiaru punktu jednostki logiczne automatycznie.

Aby uzyskać więcej informacji na temat `CFont`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cfont"></a>  CFont::CFont

Konstruuje `CFont` obiektu.

```
CFont();
```

### <a name="remarks"></a>Uwagi

Wynikowy obiekt musi zostać zainicjowany z `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, lub `CreatePointFontIndirect` zanim będzie można jej używać.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>  CFont::CreateFont

Inicjuje `CFont` obiektu o określonej charakterystyce.

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

*nHeight*<br/>
Określa żądaną wysokość (w jednostkach logicznych) czcionki. Zobacz `lfHeight` członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)struktury w zestawie Windows SDK opis. Wartość bezwzględna *nHeight* nie może przekraczać 16 384 jednostki urządzenia po konwersji. Dla porównań wysokość mapowania czcionki szuka największych czcionka, która nie przekracza żądany rozmiar lub najmniejszy wszystkie czcionki przekroczy żądany rozmiar.

*nWidth*<br/>
Określa średnią szerokość (w jednostkach logicznych), znaków w czcionce. Jeśli *nWidth* wynosi 0, współczynnik proporcji, urządzenia będą dopasowywane współczynnik proporcji digitization czcionek dostępnych można znaleźć najlepiej dopasowany, który jest określony przez wartość bezwzględna różnicy.

*nEscapement*<br/>
Określa kąt (w jednostkach stopień 0,1) między wektor escapement i osi x wyświetlanej powierzchni. Wektor escapement jest wiersza za pośrednictwem źródła pierwszy i ostatni znak w wierszu. Kąt jest zegara mierzony od osi x. Zobacz `lfEscapement` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK, aby uzyskać więcej informacji.

*nOrientation*<br/>
Określa kąt (w jednostkach stopień 0,1) między linii bazowej znaku i osi x. Kąt jest zegara mierzony od osi x dla współrzędnych, w których kierunku y jest szczegółów oraz z ruchem wskazówek zegara od osi x dla współrzędnych, w których działa kierunku y.

*nWeight*<br/>
Określa grubość czcionki (w pikselach połączone na 1000 operacji). Zobacz *lfWeight* elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK, aby uzyskać więcej informacji. Opisano wartości są przybliżone; wygląd rzeczywisty zależy od kroju czcionki. Niektóre czcionki mają tylko FW_NORMAL FW_REGULAR i FW_BOLD wagi. Jeśli FW_DONTCARE jest określony, domyślna grubość jest używany.

*bItalic*<br/>
Określa, czy czcionka jest pochylony.

*bUnderline*<br/>
Określa, czy czcionka jest podkreślony.

*cStrikeOut*<br/>
Określa, czy są wykreślić, znaki w czcionce. Określa czcionkę przekreślenie, jeśli ustawiona na wartość różną od zera.

*nCharSet*<br/>
Określa czcionkę znak setSee `lfCharSet` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości.

Zbiór znaków OEM jest zależna od systemu.

Czcionek z innych zestawów znaków może istnieć w systemie. Aplikacja, która używa czcionki z zestawem nieznany znak nie wolno próbować tłumaczenie i interpretowania ciągów, które mają być renderowany przy użyciu tego czcionki. Zamiast tego ciągi powinny przekazane bezpośrednio do wyjścia sterownika urządzenia.

Mapowanie czcionek nie korzysta z wartości DEFAULT_CHARSET. Aplikację można użyć tej wartości, aby umożliwić nazwę i rozmiar czcionki, które w pełni opisuje logiczne czcionki. Jeśli czcionki o podanej nazwie nie istnieje, można zastąpić czcionkę z dowolnego zestawu znaków określonej czcionki. Aby uniknąć nieoczekiwanych wyników, aplikacje powinny używać wartości DEFAULT_CHARSET rzadko.

*nOutPrecision*<br/>
Określa dokładność żądaną produktu wyjściowego. Dokładność danych wyjściowych definiuje, jak blisko dane wyjściowe muszą odpowiadać wysokość, szerokość, orientacja znak, escapement i pomysłu żądanej czcionki. Zobacz `lfOutPrecision` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości i uzyskać więcej informacji.

*nClipPrecision*<br/>
Określa dokładność żądaną wycinka. Dokładność wycinka definiuje sposób obcina znaki, które są częściowo spoza obszaru przycinania. Zobacz `lfClipPrecision` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości.

Aby użyć osadzona czcionka w trybie tylko do odczytu, aplikacja musi określić CLIP_ENCAPSULATE.

Uzyskanie spójnego obrót urządzenia, TrueType i czcionki wektorowe, aplikacja może użyć operatora OR połączyć wartości CLIP_LH_ANGLES z żadnym innym *nClipPrecision* wartości. Jeśli ustawiono CLIP_LH_ANGLES bit, obracanie dla wszystkich czcionek zależy od tego, czy orientację w układzie współrzędnych leworęczni lub prawostronnego układu. (Aby uzyskać więcej informacji na temat orientacji współrzędnych, zobacz opis *nOrientation* parametru.) Jeśli nie ustawiono CLIP_LH_ANGLES, czcionki urządzenia zawsze Obróć w lewo, ale obrót inne czcionki jest zależny od orientację w układzie współrzędnych.

*nQuality*<br/>
Określa jakość wyjściowa czcionki, który definiuje, jak dokładnie interfejs GDI musi podjęcia próby dopasowania atrybuty logiczne czcionki do tych rzeczywiste czcionki fizycznych. Zobacz `lfQuality` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości.

*nPitchAndFamily*<br/>
Określa gęstość i rodzinę czcionek. Zobacz `lfPitchAndFamily` elementu członkowskiego w `LOGFONT` struktury w zestawie Windows SDK dla listy wartości i uzyskać więcej informacji.

*lpszFacename*<br/>
A `CString` lub wskaźnikiem do ciągu zakończony znakiem null, który określa nazwę krój czcionki. Długość ciągu nie może przekraczać 30 znaków. Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa) funkcja może służyć do wyliczyć wszystkie aktualnie dostępne czcionki. Jeśli *lpszFacename* ma wartość NULL, interfejs GDI używa krój niezależnych od urządzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać czcionkę czcionki we wszystkich kontekstach urządzenia.

`CreateFont` Funkcja nie tworzy nową czcionkę Windows GDI. Jedynie wybiera najlepiej dopasowany z fizycznego czcionek dostępnych do interfejs GDI.

Aplikacje można użyć ustawień domyślnych dla większości parametrów, tworząc logiczne czcionki. Parametry, które zawsze powinien być podawany określone wartości są *nHeight* i *lpszFacename*. Jeśli *nHeight* i *lpszFacename* nie są ustawione przez aplikację, czcionka logicznej, która jest tworzona jest zależny od urządzenia.

Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreateFont` funkcji, należy użyć `CDC::SelectObject` wybrać czcionkę do kontekstu urządzenia, następnie usuń `CFont` obiekt, który nie jest już potrzebny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect

Inicjuje `CFont` obiekt z właściwościami w [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)struktury.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Wskazuje `LOGFONT` strukturę, która definiuje właściwości logicznej czcionki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać czcionkę jako bieżącą czcionkę dla dowolnego urządzenia.

Tę czcionkę ma właściwości określone w [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury. Po wybraniu czcionki przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcja elementu członkowskiego mapowania czcionki GDI próbuje dopasować logiczne czcionki przy użyciu istniejących czcionki fizycznych. Jeśli mapowanie czcionek nie znalezione dokładne dopasowanie dla logicznej czcionki, zapewnia alternatywną czcionki, którego charakterystyka dopasowania tyle żądanej właściwości, jak to możliwe.

Jeśli nie potrzebujesz już `CFont` obiekt utworzony przez `CreateFontIndirect` funkcji, należy użyć `CDC::SelectObject` wybrać czcionkę do kontekstu urządzenia, następnie usuń `CFont` obiekt, który nie jest już potrzebny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>  CFont::CreatePointFont

Ta funkcja udostępnia prosty sposób utworzyć czcionkę określony krój i rozmiar punktu.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*nPointSize*<br/>
Żądana wysokość czcionki w dziesiątych punktu. (Na przykład przekazać 120 żądania czcionki punktu 12).

*lpszFaceName*<br/>
A `CString` lub wskaźnikiem do ciągu zakończony znakiem null, który określa nazwę krój czcionki. Długość ciągu nie może przekraczać 30 znaków. Windows "Funkcja EnumFontFamilies można wyliczyć wszystkie aktualnie dostępne czcionki. Jeśli *lpszFaceName* ma wartość NULL, interfejs GDI używa krój niezależnych od urządzenia.

*podstawowego kontrolera domeny*<br/>
Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiekt ma być używany do przekonwertowania wysokość w *nPointSize* jednostki logiczne. Jeśli ma wartość NULL, kontekst urządzenia ekranu jest używana do konwersji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Automatycznie konwertuje wysokość w *nPointSize* jednostki logiczne za pomocą obiektu CDC wskazywany przez *kontrolera pDC*.

Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreatePointFont` funkcji, najpierw wybierz czcionkę poza kontekstem urządzenia, a następnie usuń `CFont` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

Ta funkcja jest taka sama jak [CreateFontIndirect](#createfontindirect) z tą różnicą, że `lfHeight` członkiem `LOGFONT` jest interpretowany w dziesiątych jednostek punktu, a nie urządzenia.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Wskazuje [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) strukturę, która definiuje właściwości logicznej czcionki. `lfHeight` Członkiem `LOGFONT` struktury jest mierzony w liczbę dziesiątych części punkt, a nie jednostki logiczne. (Na przykład ustawić `lfHeight` 120 żądania czcionki punktu 12.)

*podstawowego kontrolera domeny*<br/>
Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiekt ma być używany do przekonwertowania wysokość w `lfHeight` jednostki logiczne. Jeśli ma wartość NULL, kontekst urządzenia ekranu jest używana do konwersji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja powoduje automatyczną konwersję wysokość w `lfHeight` jednostki logiczne za pomocą obiektu CDC wskazywany przez *kontrolera pDC* przed przekazaniem `LOGFONT` struktury do Windows.

Po zakończeniu pracy z `CFont` obiekt utworzony przez `CreatePointFontIndirect` funkcji, najpierw wybierz czcionkę poza kontekstem urządzenia, a następnie usuń `CFont` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>  CFont::FromHandle

Zwraca wskaźnik do `CFont` obiektu, kiedy biorąc pod uwagę uchwyt HFONT obiektowi czcionki Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
HFONT obsługi na czcionkę Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFont` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CFont` obiektu nie jest już dołączony do uchwyt tymczasowego `CFont` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CFont` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, w której czas wszystkich tymczasowych grafiki obiekty zostaną usunięte. Innym sposobem powiedzenia, to jest, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jednego okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>  CFont::GetLogFont

Wywołaj tę funkcję, aby pobrać kopię `LOGFONT` struktury dla `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parametry

*pLogFont*<br/>
Wskaźnik do [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) strukturę, aby otrzymywać informacje czcionki.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli funkcja się powiedzie, w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>  HFONT CFont::operator

Użyj tego operatora, można pobrać uchwytu Windows GDI czcionki dołączone do `CFont` obiektu.

```
operator HFONT() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt obiektu czcionki Windows GDI dołączonych do `CFont` Jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ponieważ ten operator jest automatycznie używany podczas konwersji z `CFont` do [czcionek i tekstu](/windows/desktop/gdi/fonts-and-text), można przekazać `CFont` obiekty do funkcji, które oczekują HFONTs.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbki MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)



