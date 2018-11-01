---
title: Klasa CMFCToolBarFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 28b2b77ed28453f148786ba7109743a0b7baf598
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429266"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Klasa CMFCToolBarFontComboBox

Przycisk paska narzędzi, który zawiera formant pola kombi, która umożliwia użytkownikowi wybranie czcionkę z listy czcionek systemowych.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Konstruuje `CMFCToolBarFontComboBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Wybiera czcionkę w polu kombi czcionki, zgodnie z jedną nazwę czcionki lub prefiks i zestaw znaków czcionek.|

### <a name="data-members"></a>Elementy członkowskie danych

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Wysokość znaków w polu kombi czcionki.

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pole kombi czcionki na pasku narzędzi, wykonaj następujące kroki:

1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi.

1. Konstruowania `CMFCToolBarFontComboBox` obiektu.

1. Programu obsługi wiadomości, która przetwarza komunikat AFX_WM_RESETTOOLBAR, oryginalnym przycisk zastąpić nowy przycisk pola kombi przy użyciu [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronizuj czcionka, która jest wybrane w polu kombi czcionki w dokumencie za pomocą [CMFCToolBarFontComboBox::SetFont](#setfont) metody.

Aby zsynchronizować czcionki dokumentu przy użyciu czcionki wybrane w polu kombi, należy użyć [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) metody do pobierania atrybutów wybranej czcionki i używanie tych atrybutów do tworzenia [ Klasa CFont](../../mfc/reference/cfont-class.md) obiektu.

Przycisk pola kombi czcionki wywołuje funkcję Win32 [EnumFontFamiliesEx](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesexa) ustalenie czcionki ekranu i drukarki, które muszą być dostępne w systemie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Konstruuje [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) obiektu.

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Identyfikator polecenia pola kombi.

*iImage*<br/>
[in] Liczony od zera indeks obrazu paska narzędzi. Obraz, który znajduje się w [klasa CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiekt [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) przechowuje klasy.

*nFontType*<br/>
[in] Typy czcionek, które zawierają pola kombi. Ten parametr może być kombinacją (logiczne OR) następujące wartości:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Jeśli ustawienie DEFAULT_CHARSET, w polu kombi zawiera wszystkie jednoznacznie o silnych nazwach czcionki we wszystkich zestawach znaków. (Jeśli istnieją dwie czcionki o takiej samej nazwie, pole kombi zawiera jeden z nich). Jeśli ustawionym na wartość zestawu prawidłowych znaków polu kombi zawiera tylko czcionek w określonego zestawu znaków. Zobacz [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) zawiera listę możliwych znak ustawia.

*dwStyle*<br/>
[in] Style pola kombi. (zobacz [style pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] Szerokość w pikselach kontrolki edycji.

*nPitchAndFamily*<br/>
[in] Jeśli ustawienie DEFAULT_PITCH, w polu kombi zawiera czcionki, niezależnie od pomysłu. Jeśli ustawienie FIXED_PITCH lub VARIABLE_PITCH, pole kombi zawiera tylko czcionek z tym typem pomysłu. Filtrowanie oparte na rodzinę czcionek nie jest obecnie obsługiwane.

*pLstFontsExternal*<br/>
[out] Wskaźnik do [klasa CObList](../../mfc/reference/coblist-class.md) obiekt, który przechowuje dostępne czcionki.

### <a name="remarks"></a>Uwagi

Zazwyczaj `CMFCToolBarFontComboBox` obiekty przechowywania listy dostępnych czcionek w pojedyncza, współdzielona `CObList` obiektu. Jeśli używasz drugie przeciążenie konstruktora i podaj prawidłowy wskaźnik do *pLstFontsExternal*, które `CMFCToolBarFontComboBox` obiektu będzie zamiast tego podać `CObList` , *pLstFontsExternal* Wskazuje z dostępnych czcionek.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCToolBarFontComboBox` obiektu. Ten fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[in] Określa liczony od zera indeks elementu pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCFontInfo` obiektu. Jeśli *iIndex* nie określa indeks prawidłowym elementem, wartość zwracana jest wartość NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Określa wysokość w pikselach, znaków w polu kombi czcionki, jeśli pole kombi ma właściciela styl rysowania.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Uwagi

Jeśli `m_nFontHeight` zmienna ma wartość 0, wysokość jest obliczana automatycznie zgodnie z domyślną czcionkę pola kombi. Wysokość obejmuje zarówno znaków powyżej linii bazowej i zejścia znaków poniżej linii bazowej.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Wybiera czcionkę w pole kombi czcionki, zgodnie z jej nazwą i znak zestawu, które są określone w parametrach.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Określa nazwę czcionki lub prefiks.

*nCharSet*<br/>
[in] Określa zestaw znaków.

*bExact*<br/>
[in] Określa, czy *lpszName* zawiera nazwę czcionki lub prefiks czcionki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pomyślnie; wybrano czcionki w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bExact* ma wartość TRUE, ta metoda wybiera czcionkę, który dokładnie pasuje do nazwy, który został określony jako *lpszName*. Jeśli *bExact* ma wartość FAŁSZ, to wybiera metoda czcionkę, która rozpoczyna się od tekstu określony jako *lpszName* i który korzysta z zestawu znaków, który został określony jako *nCharSet*. Jeśli *nCharSet* ustawiono DEFAULT_CHARSET, zestaw znaków będzie ignorowane i tylko *lpszName* będzie służyć do wybierz czcionkę.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)

