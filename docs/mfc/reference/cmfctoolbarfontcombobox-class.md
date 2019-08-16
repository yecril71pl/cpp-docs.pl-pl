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
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504745"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Klasa CMFCToolBarFontComboBox

Przycisk paska narzędzi zawierający formant pola kombi, który umożliwia użytkownikowi wybranie czcionki z listy czcionek systemowych.

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
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Wybiera czcionkę w polu kombi czcionki według nazwy czcionki lub prefiksu i zestawu znaków czcionki.|

### <a name="data-members"></a>Elementy członkowskie danych

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Wysokość znaków w polu kombi czcionki.

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola kombi czcionki do paska narzędzi, wykonaj następujące kroki:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

1. Konstruowanie `CMFCToolBarFontComboBox` obiektu.

1. W programie obsługi komunikatów, który przetwarza komunikat AFX_WM_RESETTOOLBAR, Zastąp oryginalny przycisk nowym przyciskiem pola kombi przy użyciu [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Zsynchronizuj czcionkę wybraną w polu kombi z czcionką w dokumencie przy użyciu metody [CMFCToolBarFontComboBox:: SetFont](#setfont) .

Aby zsynchronizować czcionkę dokumentu z czcionką wybraną w polu kombi, użyj metody [CMFCToolBarFontComboBox:: GetFontDesc](#getfontdesc) , aby pobrać atrybuty wybranej czcionki i użyć tych atrybutów do utworzenia obiektu [klasy CFont](../../mfc/reference/cfont-class.md) .

Przycisk kombi czcionki wywołuje funkcję Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) , aby określić czcionki ekranu i drukarki dostępne dla systemu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox. h

##  <a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Konstruuje obiekt [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) .

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
podczas Identyfikator polecenia pola kombi.

*iImage*<br/>
podczas Indeks (liczony od zera) obrazu paska narzędzi. Obraz znajduje się w obiekcie [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) , który obsługuje Klasa klasy [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*nFontType*<br/>
podczas Typy czcionek, które zawiera pole kombi. Ten parametr może być kombinacją (Boolean lub) następujących wartości:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
podczas Jeśli ustawiona na DEFAULT_CHARSET, pole kombi zawiera wszystkie czcionki z unikatowymi nazwami we wszystkich zestawach znaków. (Jeśli istnieją dwie czcionki o tej samej nazwie, pole kombi zawiera jeden z nich). W przypadku ustawienia prawidłowej wartości zestawu znaków pole kombi zawiera tylko czcionki w określonym zestawie znaków. Zobacz [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , aby uzyskać listę możliwych zestawów znaków.

*dwStyle*<br/>
podczas Styl pola kombi. (zobacz [Style pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
podczas Szerokość kontrolki edycji w pikselach.

*nPitchAndFamily*<br/>
podczas Jeśli ustawiona na DEFAULT_PITCH, pole kombi zawiera czcionki bez względu na gęstość. W przypadku ustawienia wartości FIXED_PITCH lub VARIABLE_PITCH pole kombi zawiera tylko czcionki o tym typie. Filtrowanie na podstawie rodziny czcionek nie jest obecnie obsługiwane.

*pLstFontsExternal*<br/>
określoną Wskaźnik do obiektu [klasy CObList](../../mfc/reference/coblist-class.md) , w którym są przechowywane dostępne czcionki.

### <a name="remarks"></a>Uwagi

Zazwyczaj obiekty przechowują listę dostępnych czcionek w jednym udostępnionym `CObList` obiekcie. `CMFCToolBarFontComboBox` Jeśli używasz drugiego przeciążenia konstruktora i podajesz prawidłowy wskaźnik do *pLstFontsExternal*, ten `CMFCToolBarFontComboBox` obiekt będzie wypełniać te `CObList` punkty *pLstFontsExternal* do z dostępnymi czcionkami.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCToolBarFontComboBox` obiektu. Ten fragment kodu jest częścią [przykładu Notatnika programu Word](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Określa indeks (liczony od zera) elementu pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCFontInfo` obiektu. Jeśli *IIndex* nie określa prawidłowego indeksu elementu, zwracana wartość ma wartość null.

##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Określa wysokość (w pikselach) znaków w polu kombi czcionki, jeśli pole kombi ma styl rysowania przez właściciela.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Uwagi

`m_nFontHeight` Jeśli zmienna ma wartość 0, wysokość jest obliczana automatycznie zgodnie z domyślną czcionką pola kombi. Wysokość obejmuje zarówno wzniesienie znaków powyżej linii bazowej, jak i wynoszące znaki poniżej linii bazowej.

##  <a name="setfont"></a>CMFCToolBarFontComboBox:: SetFont

Wybiera czcionkę w polu kombi czcionki zgodnie z nazwą czcionki i zestawem znaków, które są określone w parametrach.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
podczas Określa nazwę lub prefiks czcionki.

*nCharSet*<br/>
podczas Określa zestaw znaków.

*bExact*<br/>
podczas Określa, czy *lpszName* zawiera nazwę czcionki czy prefiks czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, Jeśli czcionka została wybrana pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bExact* ma wartość true, ta metoda wybiera czcionkę, która dokładnie pasuje do nazwy określonej jako *lpszName*. Jeśli *bExact* ma wartość false, ta metoda wybiera czcionkę rozpoczynającą się od tekstu określonego jako *lpszName* i używa zestawu znaków, który został określony jako *nCharSet*. Jeśli *nCharSet* jest ustawiona na DEFAULT_CHARSET, zestaw znaków zostanie zignorowany, a tylko *lpszName* zostanie użyty do wybrania czcionki.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
