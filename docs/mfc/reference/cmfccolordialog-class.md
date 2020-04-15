---
title: Klasa CMFCColorDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 987e4f1e5e89c3c56b58adaad76cfd23d5e26c52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367719"
---
# <a name="cmfccolordialog-class"></a>Klasa CMFCColorDialog

Klasa `CMFCColorDialog` reprezentuje okno dialogowe wyboru kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Konstruuje `CMFCColorDialog` obiekt.|
|`CMFCColorDialog::~CMFCColorDialog`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Zwraca bieżący wybrany kolor.|
|[CMFCColorDialog::GetPalette](#getpalette)|Zwraca paletę kolorów.|
|`CMFCColorDialog::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. Aby uzyskać informacje dotyczące składni i innych informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CDialogEx::PreTranslateMessage`).|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Wyprowadza paletę z palety systemu.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Ustawia bieżący wybrany kolor.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Ustawia kolor najbardziej odpowiadający określonej wartości RGB.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Wybiera wartość RGB dla pierwszej strony właściwości.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Wybiera wartość RGB dla drugiej strony właściwości.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bIsMyPalette`|PRAWDA, jeśli okno dialogowe zaznaczanie kolorów używa własnej palety kolorów, lub FALSE, jeśli `CMFCColorDialog` okno dialogowe używa palety określonej w konstruktorze.|
|`m_bPickerMode`|PRAWDA, gdy użytkownik wybiera kolor z okna dialogowego zaznaczania; w przeciwnym razie FALSE.|
|`m_btnColorSelect`|Przycisk koloru wybrany przez użytkownika.|
|`m_CurrentColor`|Aktualnie wybrany kolor.|
|`m_hcurPicker`|Kursor używany do wybierania koloru.|
|`m_NewColor`|Potencjalny wybrany kolor, który można na stałe wybrać lub przywrócić do oryginalnego koloru.|
|`m_pColourSheetOne`|Wskaźnik do pierwszej strony właściwości arkusza właściwości zaznaczenia koloru.|
|`m_pColourSheetTwo`|Wskaźnik do drugiej strony właściwości arkusza właściwości zaznaczenia koloru.|
|`m_pPalette`|Bieżąca paleta logiczna.|
|`m_pPropSheet`|Wskaźnik do arkusza właściwości okna dialogowego wyboru kolorów.|
|`m_wndColors`|Obiekt sterujący selektora kolorów.|
|`m_wndStaticPlaceHolder`|Formant statyczny, który jest symbolem zastępczym dla arkusza właściwości selektora kolorów.|

## <a name="remarks"></a>Uwagi

Okno dialogowe wyboru kolorów jest wyświetlane jako arkusz właściwości z dwiema stronami. Na pierwszej stronie wybierz standardowy kolor z palety systemu; na drugiej stronie wybierz kolor niestandardowy.

Można skonstruować `CMFCColorDialog` obiekt na stosie, a następnie wywołać `DoModal`, `CMFCColorDialog` przekazując początkowy kolor jako parametr do konstruktora. Następnie w oknie dialogowym wyboru kolorów tworzy kilka obiektów [klasy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) do obsługi każdej palety kolorów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cdialogex](../../mfc/reference/cdialogex-class.md)

[Cmfccolordialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonfigurować okno `CMFCColorDialog` dialogowe kolorów przy użyciu różnych metod w klasie. W przykładzie pokazano, jak ustawić bieżące i nowe kolory okna dialogowego oraz jak ustawić czerwone, zielone i niebieskie składniki wybranego koloru na dwóch stronach właściwości okna dialogowego kolorów. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

Konstruuje `CMFCColorDialog` obiekt.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parametry

*clrJnit (clrInit)*<br/>
[w] Domyślne zaznaczenie koloru. Jeśli żadna wartość nie zostanie określona, wartością domyślną jest RGB(0,0,0) (czarny).

*Dwflags*<br/>
[w] Zastrzeżone.

*pParentWnd*<br/>
[w] Wskaźnik do okna nadrzędnego lub okna właściciela okna okna dialogowego.

*hPal (właso)*<br/>
[w] Uchwyt do palety kolorów.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFCColorDialog::GetColor

Pobiera kolor wybrany przez użytkownika z okna dialogowego kolorów.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) zawierająca informacje RGB dla koloru wybranego w oknie dialogowym kolor.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji `DoModal` po wywołaniu metody.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColorDialog::GetPalette

Pobiera paletę kolorów dostępną w bieżącym oknie dialogowym kolorów.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPalette` obiektu, który został `CMFCColorDialog` określony w konstruktorze.

### <a name="remarks"></a>Uwagi

Paleta kolorów określa kolory, które użytkownik może wybrać.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Wyprowadza paletę z palety systemu.

```
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Ustawia bieżący kolor okna dialogowego.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[w] Wartość koloru RGB

### <a name="remarks"></a>Uwagi

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Ustawia bieżący kolor na kolor w bieżącej palecie, która jest najbardziej podobna.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[w] [OdNOŚNIK KOLORÓW](/windows/win32/gdi/colorref) określający kolor RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColorDialog::SetPageOne

Jawnie określa czerwone, zielone i niebieskie składniki wybranego koloru na pierwszej stronie właściwości okna dialogowego koloru.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[w] Określa czerwony składnik wartości RGB.

*G*<br/>
[w] Określa zielony składnik wartości RGB.

*B*<br/>
[w] Określa niebieski składnik wartości RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Jawnie określa czerwone, zielone i niebieskie składniki wybranego koloru na drugiej stronie właściwości okna dialogowego koloru.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[w] Określa czerwony składnik wartości RGB

*G*<br/>
[w] Określa zielony składnik wartości RGB

*B*<br/>
[w] Określa niebieski składnik wartości RGB

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
