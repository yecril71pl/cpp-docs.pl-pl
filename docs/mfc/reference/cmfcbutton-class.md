---
title: Klasa CMFCButton
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: 5434801969a55387a5b5555c9a4ade22f1969e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367778"
---
# <a name="cmfcbutton-class"></a>Klasa CMFCButton

Klasa `CMFCButton` dodaje funkcje do [CButton](../../mfc/reference/cbutton-class.md) klasy, takie jak wyrównywanie tekstu przycisku, łączenie tekstu przycisku i obrazu, zaznaczanie kursora i określanie etykietki narzędzia.

## <a name="syntax"></a>Składnia

```
class CMFCButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Domyślny konstruktor.|
|`CMFCButton::~CMFCButton`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton::Oczyszczanie](#cleanup)|Resetuje zmienne wewnętrzne i zwalnia przydzielone zasoby, takie jak obrazy, mapy bitowe i ikony.|
|`CMFCButton::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCButton::DrawItem`|Wywoływana przez strukturę, gdy zmienił się wizualny aspekt przycisku rysowanego przez właściciela. (Zastępuje [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Określa, czy pełny tekst etykietki narzędzia ma być wyświetlany w dużym oknie etykietki narzędzia, czy obcięty tekst w małym oknie etykietki narzędzia.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Określa, czy czcionka tekstowa przycisku jest taka sama jak czcionka menu aplikacji.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Określa, czy styl obramowania przycisku odpowiada bieżącej kompozycji systemu Windows.|
|`CMFCButton::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Zwraca odwołanie do podstawowej etykietki narzędzia.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Wskazuje, czy pole wyboru lub przycisk opcji to przycisk automatyczny.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Wskazuje, czy przycisk jest ustawiony na tryb automatycznego powtarzania.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Wskazuje, czy przycisk jest przyciskiem pola wyboru.|
|[CMFCButton::CzySprawiony](#ischecked)|Wskazuje, czy bieżący przycisk jest zaznaczony.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Wskazuje, czy przycisk jest wyróżniony.|
|[CMFCButton::JestPressed](#ispressed)|Wskazuje, czy przycisk jest wciśnięta i wyróżniona.|
|[CMFCButton::IsPushed](#ispushed)|Wskazuje, czy przycisk jest wciśnięta.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Wskazuje, czy przycisk jest przyciskiem opcji.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Wskazuje, czy styl obramowania przycisku odpowiada bieżącej kompozycji systemu Windows.|
|`CMFCButton::OnDrawParentBackground`|Rysuje tło nadrzędnego przycisku w określonym obszarze. (Zastępuje [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Zastępuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Ustawia przycisk na tryb automatycznego powtarzania.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Ustawia obraz dla zaznaczonego przycisku.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Ustawia kolor tła dla tekstu przycisku.|
|[CMFCButton::SetImage](#setimage)|Ustawia obraz przycisku.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Ustawia obraz kursora.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Ustawia kursor na obraz dłoni.|
|[CMFCButton::SetStdImage](#setstdimage)|Używa `CMenuImages` obiektu do ustawiania obrazu przycisku.|
|[CMFCButton::SetTextColor](#settextcolor)|Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczony.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Ustawia kolor tekstu przycisku dla zaznaczonego przycisku.|
|[CMFCButton::SetTooltip](#settooltip)|Kojarzy etykietkę narzędzia za pomocą przycisku.|
|[CMFCButton::SizeToContent](#sizetocontent)|Rozmiar przycisku powoduje, że jest on zawierał tekst i obraz przycisku.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Wywoływana przez strukturę, aby narysować przycisk.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Wywoływana przez ramy, aby narysować obramowanie przycisku.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez strukturę, aby narysować prostokąt fokus dla przycisku.|
|[CMFCButton::OnDrawText](#ondrawtext)|Wywoływane przez ramy, aby narysować tekst przycisku.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Wywoływane przez ramy, aby narysować tło tekstu przycisku.|
|[CMFCButton::WybierzFont](#selectfont)|Pobiera czcionkę skojarzoną z określonym kontekstem urządzenia.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Określa wyrównanie tekstu przycisku.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Określa, czy mają być używane motywy systemu Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Wskazuje, czy wokół przycisku ma być rysowany prostokąt fokusu.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Określa styl przycisku, taki jak bez obramowania, płaski, pół-płaski lub 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Gdy true, umożliwia wyłączony przycisk, które mają być rysowane jako wyszarzone.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Wskazuje, czy przycisk BS_CHECKBOX stylu, gdy kursor najedzie nad nim.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Wskazuje, czy odpowiedzieć na zdarzenia przycisku w dół.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Wskazuje, czy obraz ma być wyświetlany po prawej stronie przycisku.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Wskazuje, czy obraz znajduje się na górze przycisku.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Wskazuje, czy przycisk jest przezroczysty.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Wskazuje, czy zdarzenie ostatniego kliknięcia było dwukrotnym kliknięciem.|

## <a name="remarks"></a>Uwagi

Inne typy przycisków pochodzą `CMFCButton` z klasy, takich jak [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) klasy, która `CMFCColorButton` obsługuje hiperłącza i klasy, która obsługuje okno dialogowe selektora kolorów.

`CMFCButton` Styl obiektu może być *3D,* *płaski,* *pół-płaski* lub *bez obramowania.* Tekst przycisku można wyrównać po lewej, górnej lub środkowej stronie przycisku. W czasie wykonywania można kontrolować, czy przycisk wyświetla tekst, obraz lub tekst i obraz. Można również określić, że określony obraz kursora ma być wyświetlany, gdy kursor znajduje się nad przyciskiem.

Utwórz formant przycisku bezpośrednio w kodzie lub za pomocą narzędzia **Kreatora klas MFC** i szablonu okna dialogowego. Jeśli utworzysz formant przycisku `CMFCButton` bezpośrednio, dodaj zmienną do aplikacji, a następnie wywołaj konstruktor i `Create` metody `CMFCButton` obiektu. Jeśli używasz **Kreatora klas MFC,** dodaj `CButton` zmienną do aplikacji, a `CButton` `CMFCButton`następnie zmień typ zmiennej z na .

Aby obsłużyć komunikaty powiadomień w aplikacji okna dialogowego, dodaj wpis mapy wiadomości i program obsługi zdarzeń dla każdego powiadomienia. Powiadomienia wysyłane przez `CMFCButton` obiekt są takie same jak `CButton` te wysyłane przez obiekt.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonfigurować właściwości przycisku `CMFCButton` przy użyciu różnych metod w klasie. Przykład jest częścią [próbki Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[Cmfcbutton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbutton.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFCButton::Oczyszczanie

Resetuje zmienne wewnętrzne i zwalnia przydzielone zasoby, takie jak obrazy, mapy bitowe i ikony.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Określa, czy pełny tekst etykietki narzędzia ma być wyświetlany w dużym oknie etykietki narzędzia, czy obcięty tekst w małym oknie etykietki narzędzia.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[w] PRAWDA, aby wyświetlić cały tekst; FAŁSZ, aby wyświetlić obcięty tekst.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Określa, czy czcionka tekstowa przycisku jest taka sama jak czcionka menu aplikacji.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[w] PRAWDA, aby użyć czcionki menu aplikacji jako czcionki tekstowej przycisku; FALSE, aby użyć czcionki systemowej. Wartość domyślna to PRAWDA.

*bRedraw*<br/>
[w] PRAWDA, aby od razu przerysować ekran ; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie jest używana do określania czcionki tekstowej przycisku, można określić czcionkę za pomocą metody [CWnd::SetFont.](../../mfc/reference/cwnd-class.md#setfont) Jeśli czcionka nie zostanie określona w ogóle, struktura ustawia czcionkę domyślną.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Określa, czy styl obramowania przycisku odpowiada bieżącej kompozycji systemu Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby użyć bieżącej kompozycji systemu Windows do rysowania obramowań przycisków; FALSE, aby nie używać motywu systemu Windows. Wartość domyślna to PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda ma wpływ na wszystkie przyciski `CMFCButton` w aplikacji, które są pochodną klasy.

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Zwraca odwołanie do podstawowej etykietki narzędzia.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do podstawowej etykietki narzędzia kontroli.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFCButton::IsAutoCheck

Wskazuje, czy pole wyboru lub przycisk opcji to przycisk automatyczny.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk ma styl BS_AUTOCHECKBOX lub BS_AUTORADIOBUTTON; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Wskazuje, czy przycisk jest ustawiony na tryb automatycznego powtarzania.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk jest ustawiony na tryb automatycznego powtarzania; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj [METODY CMFCButton::SetAutorepeatMode,](#setautorepeatmode) aby ustawić przycisk na tryb automatycznego powtarzania.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFCButton::IsCheckBox

Wskazuje, czy przycisk jest przyciskiem pola wyboru.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk ma styl BS_CHECKBOX lub BS_AUTOCHECKBOX; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFCButton::CzySprawiony

Wskazuje, czy bieżący przycisk jest zaznaczony.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zaznaczony jest bieżący przycisk; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Struktura używa różnych sposobów, aby wskazać, że różne rodzaje przycisków są sprawdzane. Na przykład przycisk radiowy jest sprawdzany, gdy zawiera kropkę; pole wyboru jest zaznaczone, gdy zawiera **znak X**.

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFCButton::IsHighlighted

Wskazuje, czy przycisk jest wyróżniony.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk jest wyróżniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Przycisk zostanie podświetlony, gdy mysz najedzie na przycisk.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFCButton::JestPressed

Wskazuje, czy przycisk jest wciśnięta i wyróżniona.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk jest naciśnięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFCButton::IsPushed

Wskazuje, czy przycisk jest wciśnięta.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk jest wciśnięta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFCButton::IsRadioButton

Wskazuje, czy przycisk jest przyciskiem opcji.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli styl przycisku jest BS_RADIOBUTTON lub BS_AUTORADIOBUTTON; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Wskazuje, czy styl obramowania przycisku odpowiada bieżącej kompozycji systemu Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli styl obramowania przycisku odpowiada bieżącej kompozycji systemu Windows; w przeciwnym razie FALSE.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Określa, czy podczas rysowania przycisku ma być używany motywy systemu Windows XP.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Wskazuje, czy wokół przycisku ma być rysowany prostokąt fokusu.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Uwagi

Ustaw `m_bDrawFocus` element członkowski na TRUE, aby określić, że struktura będzie rysować prostokąt fokusu wokół tekstu i obrazu przycisku, jeśli przycisk otrzyma fokus.

Konstruktor `CMFCButton` inicjuje ten element członkowski do TRUE.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Gdy true, umożliwia wyłączony przycisk, które mają być rysowane jako wyszarzone.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Wskazuje, czy przycisk BS_CHECKBOX stylu, gdy kursor najedzie nad nim.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Uwagi

Ustaw `m_bHighlightChecked` element członkowski na TRUE, aby określić, że struktura będzie podświetlać przycisk w stylu BS_CHECKBOX, gdy na niego znajduje się wskaźnik myszy.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Wskazuje, czy odpowiedzieć na zdarzenia przycisku w dół.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFCButton::m_bRightImage

Wskazuje, czy obraz ma być wyświetlany po prawej stronie przycisku.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFCButton::m_bTopImage](#m_bTopImage)

Wskazuje, czy obraz znajduje się na górze przycisku.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Uwagi

Ustaw `m_bRightImage` element członkowski na TRUE, aby określić, że w ramach będzie wyświetlany obraz przycisku po prawej stronie etykiety tekstowej przycisku.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFCButton::m_bTransparent

Wskazuje, czy przycisk jest przezroczysty.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Uwagi

Ustaw `m_bTransparent` element członkowski na TRUE, aby określić, że struktura sprawi, że przycisk będzie przezroczysty. Konstruktor `CMFCButton` inicjuje ten element członkowski do FALSE.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Określa wyrównanie tekstu przycisku.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Uwagi

Użyj jednej z `CMFCButton::AlignStyle` następujących wartości wyliczenia, aby określić wyrównanie tekstu przycisku:

|Wartość|Opis|
|-----------|-----------------|
|ALIGN_CENTER|(Domyślnie) Wyrównuje tekst przycisku do środka przycisku.|
|ALIGN_LEFT|Wyrównuje tekst przycisku do lewej strony przycisku.|
|ALIGN_RIGHT|Wyrównuje tekst przycisku do prawej strony przycisku.|

Konstruktor `CMFCButton` inicjuje ten element członkowski, aby ALIGN_CENTER.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Wskazuje, czy zdarzeniem ostatniego kliknięcia było dwukrotne kliknięcie.|

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Określa styl przycisku, taki jak bez obramowania, płaski, pół-płaski lub 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Uwagi

W poniższej `CMFCButton::m_nFlatStyle` tabeli wymieniono wartości wyliczenia określające wygląd przycisku.

|Wartość|Opis|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Domyślnie) Przycisk wydaje się mieć wysokie, trójwymiarowe boki. Po kliknięciu przycisku przycisk wydaje się być wciśnięty w głębokie wcięcie.|
|BUTTONSTYLE_FLAT|Gdy mysz nie zatrzymuje się nad przyciskiem, przycisk wydaje się być dwuwymiarowy i nie ma podniesionych boków. Gdy mysz zatrzymuje się nad przyciskiem, przycisk wydaje się mieć niskie, trójwymiarowe boki. Po kliknięciu przycisku przycisk wydaje się być wciśnięty w płytkie wcięcie.|
|BUTTONSTYLE_SEMIFLAT|Przycisk wydaje się mieć niskie, trójwymiarowe boki. Po kliknięciu przycisku przycisk wydaje się być wciśnięty w głębokie wcięcie.|
|BUTTONSTYLE_NOBORDERS|Przycisk nie ma podniesionych boków i zawsze pojawia się dwuwymiarowy. Przycisk nie wydaje się być wciśnięty do wcięcie po kliknięciu.|

Konstruktor `CMFCButton` inicjuje ten element członkowski, aby BUTTONSTYLE_3D.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `m_nFlatStyle` ustawić wartości `CMFCButton` zmiennej element członkowski w klasie. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFCButton::OnDraw

Wywoływana przez strukturę, aby narysować przycisk.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Odwołanie do prostokąta, który ogranicza przycisk.

*uiStan*<br/>
[w] Bieżący stan przycisku. Aby uzyskać więcej `itemState` informacji, zobacz element członkowski [drawitemstruct tematu struktury.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do narysowania przycisku.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Wywoływana przez ramy, aby narysować obramowanie przycisku.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
[w] Odwołanie do prostokąta, który ogranicza przycisk.

*uiStan*<br/>
[w] Bieżący stan przycisku. Aby uzyskać więcej `itemState` informacji, zobacz element członkowski [drawitemstruct tematu struktury.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do rysowania obramowania.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Wywoływane przez strukturę, aby narysować prostokąt fokus dla przycisku.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
[w] Odwołanie do prostokąta, który ogranicza przycisk.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu, aby narysować prostokąt fokusu.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFCButton::OnDrawText

Wywoływane przez ramy, aby narysować tekst przycisku.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Odwołanie do prostokąta, który ogranicza przycisk.

*strText (tekst)*<br/>
[w] Tekst do narysowania.

*żużle uiDTFlags*<br/>
[w] Flagi określające sposób formatowania tekstu. Aby uzyskać więcej informacji, zobacz *parametr nFormat* [metody CDC::DrawText.](../../mfc/reference/cdc-class.md#drawtext)

*uiStan*<br/>
[w] Zastrzeżone.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do narysowania tekstu przycisku.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCButton::OnFillBackground

Wywoływane przez ramy, aby narysować tło tekstu przycisku.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
[w] Odwołanie do prostokąta, który ogranicza przycisk.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu, aby narysować tło przycisku.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFCButton::WybierzFont

Pobiera czcionkę skojarzoną z określonym kontekstem urządzenia.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

### <a name="return-value"></a>Wartość zwracana

Zastąp tę metodę, aby użyć własnego kodu do pobrania czcionki.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Ustawia przycisk na tryb automatycznego powtarzania.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parametry

*nCzasdelaj*<br/>
[w] Liczba nieujemna, która określa interwał między wiadomościami, które są wysyłane do okna nadrzędnego. Interwał jest mierzony w milisekundach, a jego wartość domyślna wynosi 500 milisekund. Określ zero, aby wyłączyć tryb automatycznego powtarzania wiadomości.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje, że przycisk stale wysyłać WM_COMMAND wiadomości do okna nadrzędnego, aż przycisk zostanie zwolniony lub *nTimeDelay* parametr jest ustawiony na zero.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Ustawia obraz dla zaznaczonego przycisku.

```
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
[w] Uchwyt do ikony, która zawiera bitmapę i maskę dla nowego obrazu.

*bAutoDestroj*<br/>
[w] PRAWDA, aby określić, że zasoby mapy bitowej są niszczone automatycznie; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

*hIconHot (Niem.*<br/>
[w] Uchwyt do ikony, która zawiera obraz dla wybranego stanu.

*hBitmapa*<br/>
[w] Uchwyt do mapy bitowej, która zawiera obraz dla stanu nie zaznaczonego.

*hBitmapHot (własnik hbitmaphot)*<br/>
[w] Uchwyt do mapy bitowej zawierającej obraz dla wybranego stanu.

*bMap3dKolory*<br/>
[w] Określa przezroczysty kolor tła przycisku; oznacza to, że twarz przycisku. TRUE używać wartości koloru RGB(192, 192, 192); FAŁSZ, aby użyć `AFX_GLOBAL_DATA::clrBtnFace`wartości koloru zdefiniowanej przez .

*interfejs użytkownika uiBmpResId*<br/>
[w] Identyfikator zasobu dla niewybranego obrazu.

*uiBmpHotResId*<br/>
[w] Identyfikator zasobu dla wybranego obrazu.

*hIconDisabled ( hIconDisabled )*<br/>
[w] Uchwyt do ikony wyłączonego obrazu.

*hBitmapWydajne*<br/>
[w] Uchwyt do mapy bitowej, która zawiera wyłączony obraz.

*identyfikator uiBmpDsblResID*<br/>
[w] Identyfikator zasobu wyłączonej mapy bitowej.

*bAlphaBlend*<br/>
[w] PRAWDA, aby używać tylko 32-bitowych obrazów, które używają kanału alfa; FALSE, aby nie używać tylko obrazów kanałów alfa. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFCButton::SetFaceColor

Ustawia kolor tła dla tekstu przycisku.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*crFace (twarz)*<br/>
[w] Wartość koloru RGB.

*bRedraw*<br/>
[w] PRAWDA, aby natychmiast przerysować ekran ; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda służy do definiowania nowego koloru wypełnienia tła przycisku (twarzy). Należy zauważyć, że tło nie jest wypełnione, gdy [CMFCButton::m_bTransparent](#m_btransparent) zmiennej członkowskiej jest PRAWDA.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFCButton::SetImage

Ustawia obraz przycisku.

```
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
[w] Uchwyt do ikony, która zawiera bitmapę i maskę dla nowego obrazu.

*bAutoDestroj*<br/>
[w] PRAWDA, aby określić, że zasoby mapy bitowej są niszczone automatycznie; w przeciwnym razie FALSE. Wartość domyślna to PRAWDA.

*hIconHot (Niem.*<br/>
[w] Uchwyt do ikony, która zawiera obraz dla wybranego stanu.

*hBitmapa*<br/>
[w] Uchwyt do mapy bitowej, która zawiera obraz dla stanu nie zaznaczonego.

*hBitmapHot (własnik hbitmaphot)*<br/>
[w] Uchwyt do mapy bitowej zawierającej obraz dla wybranego stanu.

*interfejs użytkownika uiBmpResId*<br/>
[w] Identyfikator zasobu dla niewybranego obrazu.

*uiBmpHotResId*<br/>
[w] Identyfikator zasobu dla wybranego obrazu.

*bMap3dKolory*<br/>
[w] Określa przezroczysty kolor tła przycisku; oznacza to, że twarz przycisku. TRUE używać wartości koloru RGB(192, 192, 192); FAŁSZ, aby użyć `AFX_GLOBAL_DATA::clrBtnFace`wartości koloru zdefiniowanej przez .

*hIconDisabled ( hIconDisabled )*<br/>
[w] Uchwyt do ikony wyłączonego obrazu.

*hBitmapWydajne*<br/>
[w] Uchwyt do mapy bitowej, która zawiera wyłączony obraz.

*identyfikator uiBmpDsblResID*<br/>
[w] Identyfikator zasobu wyłączonej mapy bitowej.

*bAlphaBlend*<br/>
[w] PRAWDA, aby używać tylko 32-bitowych obrazów, które używają kanału alfa; FALSE, aby nie używać tylko obrazów kanałów alfa. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `SetImage` używać `CMFCButton` różnych wersji metody w klasie. Przykład jest częścią [próbki Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Ustawia obraz kursora.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parametry

*hcursor*<br/>
[w] Uchwyt kursora.

### <a name="remarks"></a>Uwagi

Ta metoda służy do skojarzenia obrazu kursora, takiego jak kursor ręczny, z przyciskiem. Kursor jest ładowany z zasobów aplikacji.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `SetMouseCursor` metody w `CMFCButton` klasie. Przykład jest częścią kodu w [przykładzie Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Ustawia kursor na obraz dłoni.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Uwagi

Ta metoda służy do skojarzenia obrazu kursora dłoni z przyciskiem. Kursor jest ładowany z zasobów aplikacji.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFCButton::SetStdImage

Używa `CMenuImages` obiektu do ustawiania obrazu przycisku.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Jeden z identyfikatorów obrazu przycisku, `CMenuImage::IMAGES_IDS` który jest zdefiniowany w wyliczeniu. Wartości obrazów określają obrazy, takie jak strzałki, piny i przyciski radiowe.

*Państwa*<br/>
[w] Jeden z identyfikatorów stanu obrazu przycisku, który jest zdefiniowany w wyliczeniu. `CMenuImages::IMAGE_STATE` Stany obrazu określają kolory przycisków, takie jak czarny, szary, jasnoszary, biały i ciemnoszary. Wartością domyślną jest `CMenuImages::ImageBlack`.

*idDisabled ( idDisabled )*<br/>
[w] Jeden z identyfikatorów obrazu przycisku, `CMenuImage::IMAGES_IDS` który jest zdefiniowany w wyliczeniu. Obraz wskazuje, że przycisk jest wyłączony. Wartością domyślną jest pierwszy `CMenuImages::IdArrowDown`obraz przycisku ( ).

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFCButton::SetTextColor

Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczony.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parametry

*clrTekst*<br/>
[w] Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Ustawia kolor tekstu przycisku dla zaznaczonego przycisku.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parametry

*clrTextHot (ClrTextHot)*<br/>
[w] Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFCButton::SetTooltip

Kojarzy etykietkę narzędzia za pomocą przycisku.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parametry

*tekst lpszToolTipText*<br/>
[w] Wskaźnik do tekstu etykietki narzędzia. Określ wartość NULL, aby wyłączyć etykietkę narzędzia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCButton::SizeToContent

Rozmiar przycisku powoduje, że jest on zawierał tekst i obraz przycisku.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[w] PRAWDA, aby obliczyć, ale nie zmienić, nowy rozmiar przycisku; FALSE, aby zmienić rozmiar przycisku. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CSize` który zawiera nowy rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda oblicza nowy rozmiar, który zawiera margines poziomy 10 pikseli i pionowy margines 5 pikseli.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[Klasa CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)
