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
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505300"
---
# <a name="cmfcfontcombobox-class"></a>Klasa CMFCFontComboBox

`CMFCFontComboBox` Klasa tworzy formant pola kombi, który zawiera listę czcionek.

## <a name="syntax"></a>Składnia

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Konstruuje `CMFCFontComboBox` obiekt.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Wywoływane przez platformę, by określić względne położenie nowego elementu w polu listy posortowanej bieżącej kontrolki pola kombi czcionki. (Przesłania [CComboBox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Wywoływane przez platformę, by narysować określony element w bieżącej kontrolce pola kombi czcionki. (Przesłania [CComboBox::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Pobiera informacje o aktualnie zaznaczonej czcionce.|
|`CMFCFontComboBox::MeasureItem`|Wywoływane przez platformę, aby informować okna o wymiarach pola listy w bieżącej kontrolce pola kombi czcionki. (Przesłania [CComboBox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Przesłania [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Wybiera czcionkę zgodną z określonymi kryteriami w polu kombi czcionki.|
|[CMFCFontComboBox::Setup](#setup)|Inicjuje listę elementów w polu kombi czcionki.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Wskazuje platformę, która ma być używana do rysowania etykiet elementów w bieżącej czcionce pola kombi.|

## <a name="remarks"></a>Uwagi

Aby użyć `CMFCFontComboBox` obiektu w oknie dialogowym, `CMFCFontComboBox` Dodaj zmienną do klasy okna dialogowego. Następnie w `OnInitDialog` metodzie klasy okna dialogowego Wywołaj metodę [CMFCFontComboBox:: Setup](#setup) , aby zainicjować listę elementów w kontrolce pole kombi.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxfontcombobox. h

##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Konstruuje `CMFCFontComboBox` obiekt.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Pobiera informacje o aktualnie zaznaczonej czcionce.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [klasy CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) , który opisuje czcionkę. Może mieć wartość NULL, jeśli nie wybrano żadnej czcionki w polu kombi.

### <a name="remarks"></a>Uwagi

##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Wskazuje platformę, która ma być używana do rysowania etykiet elementów w bieżącej czcionce pola kombi.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Uwagi

Ustaw dla tego elementu członkowskiego wartość TRUE, aby skierować strukturę do użycia tej samej czcionki do rysowania każdej etykiety elementu. Ustaw dla tego elementu członkowskiego wartość "fałsz", aby skierować platformę do rysowania każdej etykiety elementu z czcionką, której nazwa jest taka sama jak etykieta. Wartość domyślna tego elementu członkowskiego to FALSE.

##  <a name="selectfont"></a>CMFCFontComboBox::SelectFont

Wybiera czcionkę zgodną z określonymi kryteriami w polu kombi czcionki.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parametry

*pDesc*<br/>
podczas Wskazuje obiekt opisu czcionki.

*lpszName*<br/>
podczas Określa nazwę czcionki.

*nCharSet*<br/>
podczas Określa zestaw znaków. Wartość domyślna to DEFAULT_CHARSET. Aby uzyskać więcej informacji, zobacz `lfCharSet` element członkowski struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli element w polu kombi czcionki jest zgodny z określonym obiektem opisu czcionki lub nazwą czcionki i zestawem znaków; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj tej metody do zaznaczania i przewijania do elementu w polu kombi czcionki odpowiadającego określonej czcionce.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `SelectFont` metody `CMFCFontComboBox` w klasie. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>CMFCFontComboBox:: Setup

Inicjuje listę elementów w polu kombi czcionki.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
podczas Określa typ czcionki. Wartość domyślna to kombinacja bitowa (lub) DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.

*nCharSet*<br/>
podczas Określa zestaw znaków czcionki. Wartość domyślna to DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
podczas Określa gęstość i rodzinę czcionek. Wartość domyślna to DEFAULT_PITCH.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli pole kombi czcionki zostało pomyślnie zainicjowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda inicjuje pole kombi czcionki przez Wyliczenie aktualnie zainstalowanych czcionek, które pasują do określonych parametrów i wstawiają te nazwy czcionek w polu kombi czcionki.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `Setup` metody `CMFCFontComboBox` w klasie. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)
