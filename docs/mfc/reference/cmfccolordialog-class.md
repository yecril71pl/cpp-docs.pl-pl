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
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505340"
---
# <a name="cmfccolordialog-class"></a>Klasa CMFCColorDialog

`CMFCColorDialog` Klasa reprezentuje okno dialogowe wyboru koloru.

## <a name="syntax"></a>Składnia

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Konstruuje `CMFCColorDialog` obiekt.|
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorDialog:: GetColor](#getcolor)|Zwraca bieżący wybrany kolor.|
|[CMFCColorDialog:: getpaleta](#getpalette)|Zwraca paletę koloru.|
|`CMFCColorDialog::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Aby uzyskać informacje o składni i więcej informacji, zobacz [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CDialogEx::PreTranslateMessage`).|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Popochodzi z palety z palety systemowej.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Ustawia bieżący kolor.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Ustawia kolor najbardziej odpowiedni dla określonej wartości RGB.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Wybiera wartość RGB dla pierwszej strony właściwości.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Wybiera wartość RGB dla drugiej strony właściwości.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bIsMyPalette`|Wartość true, jeśli okno dialogowe wyboru koloru używa własnej palety kolorów lub FAŁSZ, jeśli okno dialogowe używa palety określonej w `CMFCColorDialog` konstruktorze.|
|`m_bPickerMode`|PRAWDA, gdy użytkownik wybiera kolor z okna dialogowego wyboru; w przeciwnym razie FALSE.|
|`m_btnColorSelect`|Przycisk koloru wybrany przez użytkownika.|
|`m_CurrentColor`|Aktualnie wybrany kolor.|
|`m_hcurPicker`|Kursor używany do wybrania koloru.|
|`m_NewColor`|Wybrany kolor z perspektywą, który można trwale wybrać lub przywrócić oryginalny kolor.|
|`m_pColourSheetOne`|Wskaźnik do pierwszej strony właściwości arkusza właściwości wyboru koloru.|
|`m_pColourSheetTwo`|Wskaźnik do drugiej strony właściwości arkusza właściwości wyboru koloru.|
|`m_pPalette`|Bieżąca paleta logiczna.|
|`m_pPropSheet`|Wskaźnik do arkusza właściwości okna dialogowego wyboru koloru.|
|`m_wndColors`|Obiekt formantu selektora kolorów.|
|`m_wndStaticPlaceHolder`|Statyczna kontrolka, która jest symbolem zastępczym arkusza właściwości selektora kolorów.|

## <a name="remarks"></a>Uwagi

Okno dialogowe wyboru koloru jest wyświetlane jako arkusz właściwości z dwiema stronami. Na pierwszej stronie wybierasz standardowy kolor z palety systemowej. na drugiej stronie można wybrać kolor niestandardowy.

Można skonstruować `CMFCColorDialog` obiekt na stosie, a następnie wywołać `DoModal`, przekazywać początkowy kolor `CMFCColorDialog` jako parametr do konstruktora. W oknie dialogowym Wybór koloru tworzone są kilka obiektów [klasy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) do obsługi każdej palety kolorów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konfigurowania okna dialogowego koloru przy użyciu różnych metod w `CMFCColorDialog` klasie. W przykładzie pokazano, jak ustawić bieżące i nowe kolory okna dialogowego oraz jak ustawić czerwony, zielony i niebieski składnik wybranego koloru na dwóch stronach właściwości okna dialogowego koloru. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolordialog. h

##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

Konstruuje `CMFCColorDialog` obiekt.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
podczas Domyślny wybór koloru. Jeśli żadna wartość nie zostanie określona, wartością domyślną jest RGB (0, 0, 0) (czerń).

*flagiDW*<br/>
podczas Rezerwacj.

*pParentWnd*<br/>
podczas Wskaźnik do okna dialogowego nadrzędnego lub właściciela.

*hPal*<br/>
podczas Uchwyt do palety kolorów.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getcolor"></a>CMFCColorDialog:: GetColor

Pobiera kolor wybierany przez użytkownika z okna dialogowego koloru.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) , która zawiera informacje RGB dotyczące koloru wybranego w oknie dialogowym koloru.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję po wywołaniu `DoModal` metody.

##  <a name="getpalette"></a>CMFCColorDialog:: getpaleta

Pobiera paletę kolorów, która jest dostępna w oknie dialogowym bieżący kolor.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPalette` obiektu, który został określony `CMFCColorDialog` w konstruktorze.

### <a name="remarks"></a>Uwagi

Paleta kolorów określa kolory, które użytkownik może wybrać.

##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Popochodzi z palety z palety systemowej.

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Ustawia bieżący kolor okna dialogowego.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*rgb*<br/>
podczas Wartość koloru RGB

### <a name="remarks"></a>Uwagi

##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Ustawia bieżący kolor na kolor w bieżącej palecie, który jest najbardziej podobny.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*rgb*<br/>
podczas Element [COLORREF](/windows/win32/gdi/colorref) , który określa kolor RGB.

### <a name="remarks"></a>Uwagi

##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne

Jawnie określa składniki czerwonego, zielonego i niebieskiego zaznaczonego koloru na pierwszej stronie właściwości okna dialogowego koloru.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
podczas Określa czerwony składnik wartości RGB.

*G*<br/>
podczas Określa zielony składnik wartości RGB.

*B*<br/>
podczas Określa niebieski składnik wartości RGB.

### <a name="remarks"></a>Uwagi

##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Jawnie określa składniki czerwonego, zielonego i niebieskiego zaznaczonego koloru na drugiej stronie właściwości okna dialogowego koloru.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
podczas Określa czerwony składnik wartości RGB

*G*<br/>
podczas Określa zielony składnik wartości RGB

*B*<br/>
podczas Określa niebieski składnik wartości RGB

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
