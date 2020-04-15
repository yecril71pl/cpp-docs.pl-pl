---
title: Klasa CMFCFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367492"
---
# <a name="cmfcfontcombobox-class"></a>Klasa CMFCFontComboBox

Klasa `CMFCFontComboBox` tworzy formant pola kombi, który zawiera listę czcionek.

## <a name="syntax"></a>Składnia

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Konstruuje `CMFCFontComboBox` obiekt.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Wywoływane przez strukturę w celu określenia względnej pozycji nowego elementu w posortowanym polu listy bieżącego formantu pola kombi czcionki. (Zastępuje [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Wywoływane przez strukturę, aby narysować określony element w bieżącym formancie pola kombi czcionki. (Zastępuje [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Pobiera informacje o aktualnie wybranej czcionce.|
|`CMFCFontComboBox::MeasureItem`|Wywoływane przez strukturę, aby poinformować system Windows o wymiarach pola listy w bieżącym formancie pola kombi czcionki. (Zastępuje [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Zastępuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::WybierzFont](#selectfont)|Wybiera czcionkę, która spełnia określone kryteria z pola kombi czcionki.|
|[CMFCFontComboBox::Konfiguracja](#setup)|Inicjuje listę elementów w polu kombi czcionki.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Wskazuje strukturę, której czcionki ma być używana do rysowania etykiet elementów w bieżącym polu kombi czcionki.|

## <a name="remarks"></a>Uwagi

Aby użyć `CMFCFontComboBox` obiektu w oknie dialogowym, dodaj zmienną `CMFCFontComboBox` do klasy okna dialogowego. Następnie w `OnInitDialog` metodzie klasy okna dialogowego wywołaj [metodę CMFCFontComboBox::Setup,](#setup) aby zainicjować listę elementów w formancie pola kombi.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccombobox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxfontcombobox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Konstruuje `CMFCFontComboBox` obiekt.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Pobiera informacje o aktualnie wybranej czcionce.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu klasy CMFCFontInfo,](../../mfc/reference/cmfcfontinfo-class.md) który opisuje czcionkę. Może mieć wartość NULL, jeśli w polu kombi nie wybrano żadnej czcionki.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Wskazuje strukturę, której czcionki ma być używana do rysowania etykiet elementów w bieżącym polu kombi czcionki.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Uwagi

Ustaw ten element członkowski na TRUE, aby skierować strukturę do używania tej samej czcionki do rysowania etykiety każdego elementu. Ustaw ten element członkowski na FALSE, aby skierować strukturę, aby narysować etykietę każdego elementu czcionką, której nazwa jest taka sama jak etykieta. Domyślną wartością tego elementu członkowskiego jest FAŁSZ.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::WybierzFont

Wybiera czcionkę, która spełnia określone kryteria z pola kombi czcionki.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parametry

*pDesc (ps.*<br/>
[w] Wskazuje obiekt opisu czcionki.

*Lpszname*<br/>
[w] Określa nazwę czcionki.

*nCharSet (Zestaw chybianie)*<br/>
[w] Określa zestaw znaków. Wartość domyślna jest DEFAULT_CHARSET. Aby uzyskać więcej `lfCharSet` informacji, zobacz element członkowski struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli element w polu kombi czcionki pasuje do określonego obiektu opisu czcionki lub nazwy czcionki i zestawu znaków; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda służy do wybierania i przewijania do elementu w polu kombi czcionki, który odpowiada określonej czcionce.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `SelectFont` metody w `CMFCFontComboBox` klasie. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Konfiguracja

Inicjuje listę elementów w polu kombi czcionki.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType (typ nFontType)*<br/>
[w] Określa typ czcionki. Wartością domyślną jest kombinacja bitowa (OR) DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.

*nCharSet (Zestaw chybianie)*<br/>
[w] Określa zestaw znaków czcionki. Wartość domyślna jest DEFAULT_CHARSET.

*nPitchAndRodzina*<br/>
[w] Określa wysokość czcionki i rodzinę. Wartość domyślna jest DEFAULT_PITCH.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pole kombi czcionki zostało pomyślnie zainicjowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda inicjuje pole kombi czcionki, wyliczając aktualnie zainstalowane czcionki, które pasują do określonych parametrów, i wstawiając te nazwy czcionek w polu kombi czcionki.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `Setup` metody w `CMFCFontComboBox` klasie. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)
