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
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360466"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Klasa CMFCToolBarFontComboBox

Przycisk paska narzędzi zawierający kontrolkę pola kombi, która umożliwia użytkownikowi wybranie czcionki z listy czcionek systemowych.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Konstruuje `CMFCToolBarFontComboBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Wybiera czcionkę w polu kombi czcionki zgodnie z nazwą czcionki lub prefiksem i zestawem znaków czcionki.|

### <a name="data-members"></a>Elementy członkowskie danych

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Wysokość znaków w polu kombi czcionki.

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola kombi czcionki do paska narzędzi, wykonaj następujące czynności:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

1. Konstruuj `CMFCToolBarFontComboBox` obiekt.

1. W programie obsługi wiadomości, który przetwarza komunikat AFX_WM_RESETTOOLBAR, zastąp oryginalny przycisk nowym przyciskiem pola kombi za pomocą [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Zsynchronizuj czcionkę wybraną w polu kombi z czcionką w dokumencie za pomocą metody [CMFCToolBarFontComboBox::SetFont.](#setfont)

Aby zsynchronizować czcionkę dokumentu z czcionką wybraną w polu kombi, użyj metody [CMFCToolBarFontComboBox::GetFontDesc,](#getfontdesc) aby pobrać atrybuty wybranej czcionki i użyć tych atrybutów do utworzenia obiektu [klasy CFont.](../../mfc/reference/cfont-class.md)

Przycisk pola kombi czcionki wywołuje funkcję Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) w celu określenia ekranu i czcionek drukarki dostępnych dla systemu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarcomboboxbutton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[Cmfctoolbarfontcombobox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Konstruuje [obiekt CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

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

*Uiid*<br/>
[w] Identyfikator polecenia pola kombi.

*Iimage*<br/>
[w] Indeks od zera obrazu paska narzędzi. Obraz znajduje się w [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md) obiektu, który [cmfctoolbar klasy](../../mfc/reference/cmfctoolbar-class.md) utrzymuje.

*nFontType (typ nFontType)*<br/>
[w] Typy czcionek, które zawiera pole kombi. Ten parametr może być kombinacją (wartość logiczna LUB) następujących wartości:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet (Zestaw chybianie)*<br/>
[w] Jeśli ustawiono DEFAULT_CHARSET, pole kombi zawiera wszystkie czcionki o unikatowej nazwie we wszystkich zestawach znaków. (Jeśli istnieją dwie czcionki o tej samej nazwie, pole kombi zawiera jedną z nich). Jeśli ustawiona jest prawidłowa wartość zestawu znaków, pole kombi zawiera tylko czcionki w określonym zestawie znaków. Zobacz [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) aby zapoznać się z listą możliwych zestawów znaków.

*Dwstyle*<br/>
[w] Styl pola kombi. (patrz [Style kombi)](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

*iWidth ( iWidth )*<br/>
[w] Szerokość w pikselach formantu edycji.

*nPitchAndRodzina*<br/>
[w] Jeśli ustawiono DEFAULT_PITCH, pole kombi zawiera czcionki niezależnie od wysokości. Jeśli ustawiono FIXED_PITCH lub VARIABLE_PITCH, pole kombi zawiera tylko czcionki o tym typie skoku. Filtrowanie na podstawie rodziny czcionek nie jest obecnie obsługiwane.

*pLstFontsNiestostna*<br/>
[na zewnątrz] Wskaźnik do [CObList Class](../../mfc/reference/coblist-class.md) obiektu, który przechowuje dostępne czcionki.

### <a name="remarks"></a>Uwagi

Zazwyczaj `CMFCToolBarFontComboBox` obiekty przechowują listę dostępnych czcionek `CObList` w jednym obiekcie udostępnionym. Jeśli użyjesz drugiego przeciążenia konstruktora i podasz prawidłowy wskaźnik `CMFCToolBarFontComboBox` do *pLstFontsExternal*, ten obiekt zamiast tego wypełni `CObList` ten *pLstFontsExternal* za pomocą dostępnych czcionek.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCToolBarFontComboBox` obiekt. Ten fragment kodu jest częścią [przykładu word pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Określa indeks od zera elementu pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCFontInfo` obiektu. Jeśli *program iIndex* nie określa prawidłowego indeksu elementów, zwracaną wartością jest NULL.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Określa wysokość znaków w pikselach w polu kombi czcionki, jeśli pole kombi ma styl rysowania właściciela.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Uwagi

Jeśli `m_nFontHeight` zmienna wynosi 0, wysokość jest obliczana automatycznie zgodnie z domyślną czcionką pola kombi. Wysokość obejmuje zarówno wznoszenie się znaków powyżej linii bazowej, jak i zejście znaków pod linią bazową.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Wybiera czcionkę w polu kombi czcionki zgodnie z nazwą czcionki i zestawem znaków, które są określone w parametrach.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
[w] Określa nazwę czcionki lub prefiks.

*nCharSet (Zestaw chybianie)*<br/>
[w] Określa zestaw znaków.

*bEkstycznie*<br/>
[w] Określa, czy *lpszName* zawiera nazwę czcionki, czy prefiks czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli czcionka została wybrana pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bExact* ma wartość PRAWDA, ta metoda wybiera czcionkę, która dokładnie odpowiada nazwie określonej jako *lpszName*. Jeśli *bExact* jest FALSE, ta metoda wybiera czcionkę, która zaczyna się od tekstu określonego jako *lpszName* i który używa zestawu znaków, który został określony jako *nCharSet*. Jeśli *nCharSet* jest ustawiony na DEFAULT_CHARSET, zestaw znaków zostanie zignorowany i tylko *lpszName* będzie używany do wybierania czcionki.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
