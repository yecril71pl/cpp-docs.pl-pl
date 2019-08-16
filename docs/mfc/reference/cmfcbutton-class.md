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
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505861"
---
# <a name="cmfcbutton-class"></a>Klasa CMFCButton

Klasa dodaje funkcje do klasy CButton, takie jak wyrównywanie tekstu przycisku, łączenie tekstu przycisku i obrazu, wybieranie kursora i określanie etykietki narzędzia. [](../../mfc/reference/cbutton-class.md) `CMFCButton`

## <a name="syntax"></a>Składnia

```
class CMFCButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Konstruktor domyślny.|
|`CMFCButton::~CMFCButton`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton:: CleanUp](#cleanup)|Resetuje zmienne wewnętrzne i zwalnia przydzieloną zasoby, takie jak obrazy, mapy bitowe i ikony.|
|`CMFCButton::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCButton::DrawItem`|Wywoływane przez platformę, gdy wizualny aspekt przycisku rysowanego przez właściciela został zmieniony. (Przesłania [CButton::D rawitem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Określa, czy wyświetlać pełny tekst etykietki narzędzia w oknie dużego etykietki narzędzi lub obcięta wersja tekstu w małym oknie etykietki narzędzia.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Określa, czy czcionka tekstu przycisku jest taka sama jak czcionka menu aplikacji.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Określa, czy styl obramowania przycisku odpowiada bieżącemu motywowi systemu Windows.|
|`CMFCButton::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Zwraca odwołanie do źródłowej kontrolki ToolTip.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Wskazuje, czy pole wyboru lub przycisk radiowy są przyciskiem automatycznym.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Wskazuje, czy przycisk jest ustawiony na tryb autopowtarzania.|
|[CMFCButton:: ischeckbox](#ischeckbox)|Wskazuje, czy przycisk jest przyciskiem pola wyboru.|
|[CMFCButton:: IsChecked](#ischecked)|Wskazuje, czy bieżący przycisk jest zaznaczony.|
|[CMFCButton:: ispodświetlacz](#ishighlighted)|Wskazuje, czy przycisk jest wyróżniony.|
|[CMFCButton:: ispressd](#ispressed)|Wskazuje, czy przycisk jest wypchnięci i wyróżniony.|
|[CMFCButton:: ispushd](#ispushed)|Wskazuje, czy przycisk jest wypychany.|
|[CMFCButton:: isradiobutton](#isradiobutton)|Wskazuje, czy przycisk jest przyciskiem radiowym.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Wskazuje, czy styl obramowania przycisku odpowiada bieżącemu motywowi systemu Windows.|
|`CMFCButton::OnDrawParentBackground`|Rysuje tło elementu nadrzędnego przycisku w określonym obszarze. (Przesłania [AFX_GLOBAL_DATA::D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Przesłania [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Ustawia przycisk na tryb autopowtarzania.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Ustawia obraz dla zaznaczonego przycisku.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Ustawia kolor tła dla tekstu przycisku.|
|[CMFCButton::SetImage](#setimage)|Ustawia obraz dla przycisku.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Ustawia obraz kursora.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Ustawia kursor na obraz dłoni.|
|[CMFCButton::SetStdImage](#setstdimage)|`CMenuImages` Używa obiektu do ustawienia obrazu przycisku.|
|[CMFCButton::SetTextColor](#settextcolor)|Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczony.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Ustawia kolor tekstu przycisku dla wybranego przycisku.|
|[CMFCButton:: SetToolTip — etykietka narzędzia](#settooltip)|Kojarzy etykietkę narzędzia z przyciskiem.|
|[CMFCButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku, aby zawierał jego tekst i obraz przycisku.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton:: OnDraw](#ondraw)|Wywoływane przez platformę, by narysować przycisk.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Wywoływane przez platformę, by narysować obramowanie przycisku.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę, aby narysować prostokąt fokusu dla przycisku.|
|[CMFCButton::OnDrawText](#ondrawtext)|Wywoływane przez platformę, by narysować tekst przycisku.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Wywoływane przez platformę, by narysować tło tekstu przycisku.|
|[CMFCButton::SelectFont](#selectfont)|Pobiera czcionkę skojarzoną z określonym kontekstem urządzenia.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Określa wyrównanie tekstu przycisku.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Określa, czy mają być używane motywy systemu Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Wskazuje, czy prostokąt fokusu ma być rysowany wokół przycisku.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Określa styl przycisku, np. bez obramowania, płaski, częściowo płaski lub 3W.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Gdy ma wartość TRUE, włącza przycisk wyłączony jako wyszarzony.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Wskazuje, czy przycisk stylu BS_CHECKBOX ma być wyróżniony po umieszczeniu kursora nad nim kursorem.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Wskazuje, czy reagować na zdarzenia przycisku w dół.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Wskazuje, czy obraz znajduje się w górnej części przycisku.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Wskazuje, czy przycisk jest przezroczysty.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Wskazuje, czy ostatnie zdarzenie kliknięcia było dwukrotne kliknięciem.|

## <a name="remarks"></a>Uwagi

Inne typy przycisków są wyprowadzane z `CMFCButton` klasy, takiej jak Klasa [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) , która obsługuje `CMFCColorButton` hiperlinki i Klasa, która obsługuje okno dialogowe selektora kolorów.

Styl `CMFCButton` obiektu może być trójwymiarowy, *płaski*, *częściowo płaski* lub *bez obramowania*. Tekst przycisku można wyrównać w lewym, górnym lub środkowym przycisku. W czasie wykonywania można kontrolować, czy przycisk wyświetla tekst, obraz, czy tekst i obraz. Możesz również określić, że określony obraz kursora będzie wyświetlany po umieszczeniu kursora na przycisku.

Utwórz kontrolkę przycisku bezpośrednio w kodzie lub przy użyciu narzędzia **kreatora klas MFC** i szablonu okna dialogowego. Jeśli utworzysz kontrolkę przycisk bezpośrednio, Dodaj `CMFCButton` zmienną do aplikacji, a następnie Wywołaj konstruktora i `Create` metody `CMFCButton` obiektu. Jeśli używasz **kreatora klas MFC**, Dodaj `CButton` zmienną do aplikacji, a następnie zmień typ zmiennej z `CButton` na `CMFCButton`.

Aby obsłużyć komunikaty powiadomień w aplikacji okna dialogowego, Dodaj wpis mapy komunikatów oraz procedurę obsługi zdarzeń dla każdego powiadomienia. Powiadomienia wysyłane przez `CMFCButton` obiekt są takie same jak te wysyłane `CButton` przez obiekt.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konfigurowania właściwości przycisku przy użyciu różnych metod w `CMFCButton` klasie. Przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbutton. h

##  <a name="cleanup"></a>CMFCButton:: CleanUp

Resetuje zmienne wewnętrzne i zwalnia przydzieloną zasoby, takie jak obrazy, mapy bitowe i ikony.

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Określa, czy wyświetlać pełny tekst etykietki narzędzia w oknie dużego etykietki narzędzi lub obcięta wersja tekstu w małym oknie etykietki narzędzia.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
podczas TRUE, aby wyświetlić cały tekst; Wartość FALSE, aby wyświetlić obcięty tekst.

### <a name="remarks"></a>Uwagi

##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Określa, czy czcionka tekstu przycisku jest taka sama jak czcionka menu aplikacji.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
podczas TRUE, aby użyć czcionki menu aplikacji jako czcionki tekstu przycisku; Wartość FALSE, aby użyć czcionki systemowej. Wartość domyślna to TRUE.

*bRedraw*<br/>
podczas Wartość TRUE powoduje natychmiastowe odświeżenie ekranu; w przeciwnym razie FALSE. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie zostanie użyta do określenia czcionki tekstu przycisku, można określić czcionkę przy użyciu metody [CWnd:: SetFont](../../mfc/reference/cwnd-class.md#setfont) . Jeśli nie określisz czcionki w ogóle, struktura ustawia domyślną czcionkę.

##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Określa, czy styl obramowania przycisku odpowiada bieżącemu motywowi systemu Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas PRAWDA, aby użyć bieżącego motywu systemu Windows do rysowania obramowań przycisków; Wartość FALSE, aby nie używać motywu systemu Windows. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda ma wpływ na wszystkie przyciski w aplikacji, które pochodzą z `CMFCButton` klasy.

##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Zwraca odwołanie do źródłowej kontrolki ToolTip.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do źródłowej kontrolki ToolTip.

### <a name="remarks"></a>Uwagi

##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck

Wskazuje, czy pole wyboru lub przycisk radiowy są przyciskiem automatycznym.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli przycisk ma styl BS_AUTOCHECKBOX lub BS_AUTORADIOBUTTON; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Wskazuje, czy przycisk jest ustawiony na tryb autopowtarzania.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli przycisk jest ustawiony na tryb autopowtarzania; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj metody [CMFCButton:: SetAutorepeatMode](#setautorepeatmode) , aby ustawić przycisk na tryb autopowtarzania.

##  <a name="ischeckbox"></a>CMFCButton:: ischeckbox

Wskazuje, czy przycisk jest przyciskiem pola wyboru.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk ma styl BS_CHECKBOX lub BS_AUTOCHECKBOX; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ischecked"></a>CMFCButton:: IsChecked

Wskazuje, czy bieżący przycisk jest zaznaczony.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżący przycisk jest zaznaczony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Struktura używa różnych sposobów, aby wskazać, że są zaznaczone różne rodzaje przycisków. Na przykład przycisk radiowy jest sprawdzany, gdy zawiera kropkę; pole wyboru jest zaznaczone, gdy zawiera **symbol X**.

##  <a name="ishighlighted"></a>CMFCButton:: ispodświetlacz

Wskazuje, czy przycisk jest wyróżniony.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk jest wyróżniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Przycisk zostanie wyróżniony po umieszczeniu wskaźnika myszy nad przyciskiem.

##  <a name="ispressed"></a>CMFCButton:: ispressd

Wskazuje, czy przycisk jest wypchnięci i wyróżniony.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk jest wciśnięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ispushed"></a>CMFCButton:: ispushd

Wskazuje, czy przycisk jest wypychany.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk jest wypchnięci; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="isradiobutton"></a>CMFCButton:: isradiobutton

Wskazuje, czy przycisk jest przyciskiem radiowym.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli stylem przycisku jest BS_RADIOBUTTON lub BS_AUTORADIOBUTTON; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Wskazuje, czy styl obramowania przycisku odpowiada bieżącemu motywowi systemu Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli styl obramowania przycisku odpowiada bieżącemu motywowi systemu Windows; w przeciwnym razie FALSE.

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Określa, czy podczas rysowania przycisku mają być używane motywy systemu Windows XP.

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Wskazuje, czy prostokąt fokusu ma być rysowany wokół przycisku.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Uwagi

`m_bDrawFocus` Ustaw element członkowski na wartość true, aby określić, że struktura będzie rysować prostokąt fokus wokół tekstu i obrazu przycisku, jeśli przycisk odbierze fokus.

`CMFCButton` Konstruktor inicjuje ten element członkowski jako wartość true.

##  <a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Gdy ma wartość TRUE, włącza przycisk wyłączony jako wyszarzony.

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Wskazuje, czy przycisk stylu BS_CHECKBOX ma być wyróżniony po umieszczeniu kursora nad nim kursorem.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Uwagi

Ustaw dla `m_bHighlightChecked` elementu członkowskiego wartość true, aby określić, że struktura będzie wyróżnić przycisk BS_CHECKBOX, gdy wskaźnik myszy jest przesuwany nad nią.

##  <a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Wskazuje, czy reagować na zdarzenia przycisku w dół.

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage

Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>CMFCButton:: m_bTopImage] (#m_bTopImage)

Wskazuje, czy obraz znajduje się w górnej części przycisku.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Uwagi

`m_bRightImage` Ustaw element członkowski na wartość true, aby określić, że struktura będzie wyświetlać obraz przycisku z prawej strony etykiety tekstowej przycisku.

##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent

Wskazuje, czy przycisk jest przezroczysty.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Uwagi

`m_bTransparent` Ustaw element członkowski na wartość true, aby określić, że struktura ma być przezroczysty. `CMFCButton` Konstruktor inicjuje ten element członkowski na wartość false.

##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Określa wyrównanie tekstu przycisku.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Uwagi

Użyj jednej z następujących `CMFCButton::AlignStyle` wartości wyliczenia, aby określić wyrównanie tekstu przycisku:

|Wartość|Opis|
|-----------|-----------------|
|ALIGN_CENTER|Wartooć Wyrównuje tekst przycisku do środka przycisku.|
|ALIGN_LEFT|Wyrównuje tekst przycisku po lewej stronie przycisku.|
|ALIGN_RIGHT|Wyrównuje tekst przycisku po prawej stronie przycisku.|

`CMFCButton` Konstruktor inicjuje ten element członkowski do ALIGN_CENTER.

##  <a name="m_bWasDblClk"></a>CMFCButton:: m_bWasDblClk] (#m_bWasDblClk) |

Wskazuje, czy ostatnie zdarzenie kliknięcia było dwukrotne kliknięciem. |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Określa styl przycisku, np. bez obramowania, płaski, częściowo płaski lub 3W.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę `CMFCButton::m_nFlatStyle` wartości wyliczenia, które określają wygląd przycisku.

|Wartość|Opis|
|-----------|-----------------|
|BUTTONSTYLE_3D|Wartooć Przycisk wydaje się mieć wysokie, trójwymiarowe boki. Gdy przycisk zostanie kliknięty, pojawi się przycisk, który zostanie naciśnięty do głębokiego wcięcia.|
|BUTTONSTYLE_FLAT|Gdy mysz nie zostanie wstrzymana nad przyciskiem, przycisk wydaje się być dwuwymiarowy i nie ma podniesionych boków. Gdy mysz zostanie zatrzymana nad przyciskiem, pojawi się przycisk z niską trójwymiarową krawędzią. Gdy przycisk zostanie kliknięty, pojawi się przycisk, który jest wciśnięty do płytki z wcięciem.|
|BUTTONSTYLE_SEMIFLAT|Wydaje się, że na przycisku występują małe i trójwymiarowe strony. Gdy przycisk zostanie kliknięty, pojawi się przycisk, który zostanie naciśnięty do głębokiego wcięcia.|
|BUTTONSTYLE_NOBORDERS|Przycisk nie ma podniesionych boków i zawsze występuje dwuwymiarowy. Po kliknięciu przycisku nie pojawia się on w formie wcięcia.|

`CMFCButton` Konstruktor inicjuje ten element członkowski do BUTTONSTYLE_3D.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób ustawiania wartości `m_nFlatStyle` zmiennej składowej `CMFCButton` w klasie. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>CMFCButton:: OnDraw

Wywoływane przez platformę, by narysować przycisk.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Odwołanie do prostokąta powiązanego z przyciskiem.

*uiState*<br/>
podczas Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` element członkowski [struktury DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do rysowania przycisku.

##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Wywoływane przez platformę, by narysować obramowanie przycisku.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
podczas Odwołanie do prostokąta powiązanego z przyciskiem.

*uiState*<br/>
podczas Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` element członkowski [struktury DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do narysowania obramowania.

##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Wywoływane przez platformę, aby narysować prostokąt fokusu dla przycisku.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
podczas Odwołanie do prostokąta powiązanego z przyciskiem.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do rysowania prostokąta fokusu.

##  <a name="ondrawtext"></a>CMFCButton::OnDrawText

Wywoływane przez platformę, by narysować tekst przycisku.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Odwołanie do prostokąta powiązanego z przyciskiem.

*strText*<br/>
podczas Tekst do narysowania.

*uiDTFlags*<br/>
podczas Flagi określające sposób formatowania tekstu. Aby uzyskać więcej informacji, zobacz *nFormat* parametru metody [przechwytywania::D rawtext](../../mfc/reference/cdc-class.md#drawtext) .

*uiState*<br/>
podczas Rezerwacj.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do rysowania tekstu przycisku.

##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground

Wywoływane przez platformę, by narysować tło tekstu przycisku.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
podczas Odwołanie do prostokąta powiązanego z przyciskiem.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby użyć własnego kodu do rysowania tła przycisku.

##  <a name="selectfont"></a>CMFCButton::SelectFont

Pobiera czcionkę skojarzoną z określonym kontekstem urządzenia.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

### <a name="return-value"></a>Wartość zwracana

Zastąp tę metodę, aby użyć własnego kodu do pobrania czcionki.

### <a name="remarks"></a>Uwagi

##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Ustawia przycisk na tryb autopowtarzania.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parametry

*nTimeDelay*<br/>
podczas Liczba nieujemna określająca interwał między komunikatami wysyłanymi do okna nadrzędnego. Interwał jest mierzony w milisekundach, a jego wartość domyślna to 500 milisekund. Określ wartość zero, aby wyłączyć tryb monitu o Autopowtarzanie.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje, że przycisk ma stale wysyłać komunikaty WM_COMMAND do okna nadrzędnego do momentu zwolnienia przycisku lub wartość parametru *nTimeDelay* jest równa zero.

##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

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

*hIcon*<br/>
podczas Dojście do ikony zawierającej mapę bitową i maskę dla nowego obrazu.

*bAutoDestroy*<br/>
podczas Wartość TRUE, aby określić, że zasoby mapy bitowej mają być automatycznie niszczone; w przeciwnym razie FALSE. Wartość domyślna to TRUE.

*hIconHot*<br/>
podczas Dojście do ikony zawierającej obraz wybranego stanu.

*hBitmap*<br/>
podczas Dojście do mapy bitowej, która zawiera obraz dla niewybranego stanu.

*hBitmapHot*<br/>
podczas Dojście do mapy bitowej, która zawiera obraz dla wybranego stanu.

*bMap3dColors*<br/>
podczas Określa przezroczysty kolor tła przycisku; oznacza to, że jest to pierwszy plan przycisku. TRUE, aby użyć wartości koloru RGB (192, 192, 192); Wartość FALSE, aby użyć wartości Color zdefiniowanej przez `AFX_GLOBAL_DATA::clrBtnFace`.

*uiBmpResId*<br/>
podczas Identyfikator zasobu dla niewybranego obrazu.

*uiBmpHotResId*<br/>
podczas Identyfikator zasobu dla wybranego obrazu.

*hIconDisabled*<br/>
podczas Dojście do ikony dla wyłączonego obrazu.

*hBitmapDisabled*<br/>
podczas Dojście do mapy bitowej zawierającej wyłączony obraz.

*uiBmpDsblResID*<br/>
podczas Identyfikator zasobu wyłączonej mapy bitowej.

*bAlphaBlend*<br/>
podczas TRUE, aby używać tylko obrazów 32-bitowych, które używają kanału alfa; Wartość FALSE, aby nie używać tylko obrazów kanału alfa. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor

Ustawia kolor tła dla tekstu przycisku.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*crFace*<br/>
podczas Wartość koloru RGB.

*bRedraw*<br/>
podczas TRUE, aby natychmiast ponownie narysować ekran; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zdefiniować nowy kolor wypełnienia tła przycisku (na przykład). Należy zauważyć, że tło nie jest wypełniane, gdy zmienna członkowska [CMFCButton:: m_bTransparent](#m_btransparent) ma wartość true.

##  <a name="setimage"></a>CMFCButton:: SetImage

Ustawia obraz dla przycisku.

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

*hIcon*<br/>
podczas Dojście do ikony zawierającej mapę bitową i maskę dla nowego obrazu.

*bAutoDestroy*<br/>
podczas Wartość TRUE, aby określić, że zasoby mapy bitowej mają być automatycznie niszczone; w przeciwnym razie FALSE. Wartość domyślna to TRUE.

*hIconHot*<br/>
podczas Dojście do ikony zawierającej obraz wybranego stanu.

*hBitmap*<br/>
podczas Dojście do mapy bitowej, która zawiera obraz dla niewybranego stanu.

*hBitmapHot*<br/>
podczas Dojście do mapy bitowej, która zawiera obraz dla wybranego stanu.

*uiBmpResId*<br/>
podczas Identyfikator zasobu dla niewybranego obrazu.

*uiBmpHotResId*<br/>
podczas Identyfikator zasobu dla wybranego obrazu.

*bMap3dColors*<br/>
podczas Określa przezroczysty kolor tła przycisku; oznacza to, że jest to pierwszy plan przycisku. TRUE, aby użyć wartości koloru RGB (192, 192, 192); Wartość FALSE, aby użyć wartości Color zdefiniowanej przez `AFX_GLOBAL_DATA::clrBtnFace`.

*hIconDisabled*<br/>
podczas Dojście do ikony dla wyłączonego obrazu.

*hBitmapDisabled*<br/>
podczas Dojście do mapy bitowej zawierającej wyłączony obraz.

*uiBmpDsblResID*<br/>
podczas Identyfikator zasobu wyłączonej mapy bitowej.

*bAlphaBlend*<br/>
podczas TRUE, aby używać tylko obrazów 32-bitowych, które używają kanału alfa; Wartość FALSE, aby nie używać tylko obrazów kanału alfa. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać różnych wersji `SetImage` metody `CMFCButton` w klasie. Przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Ustawia obraz kursora.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parametry

*hcursor*<br/>
podczas Uchwyt kursora.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby skojarzyć obraz kursora, taki jak kursor dłoni z przyciskiem. Kursor jest ładowany z zasobów aplikacji.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `SetMouseCursor` metody `CMFCButton` w klasie. Przykład jest częścią kodu w [nowych kontrolkach](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Ustawia kursor na obraz dłoni.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby skojarzyć obraz kursora z przyciskiem. Kursor jest ładowany z zasobów aplikacji.

##  <a name="setstdimage"></a>CMFCButton::SetStdImage

`CMenuImages` Używa obiektu do ustawienia obrazu przycisku.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Jeden z identyfikatorów obrazu przycisku, który jest zdefiniowany w `CMenuImage::IMAGES_IDS` wyliczeniu. Wartości obrazu określają obrazy, takie jak strzałki, numery PIN i przyciski radiowe.

*state*<br/>
podczas Jeden z identyfikatorów stanu obrazu przycisku, który jest zdefiniowany w `CMenuImages::IMAGE_STATE` wyliczeniu. Stany obrazu określają kolory przycisków, takie jak czerń, szary, jasnoszary, biały i ciemnoszary. Wartość domyślna to `CMenuImages::ImageBlack`.

*idDisabled*<br/>
podczas Jeden z identyfikatorów obrazu przycisku, który jest zdefiniowany w `CMenuImage::IMAGES_IDS` wyliczeniu. Obraz wskazuje, że przycisk jest wyłączony. Wartość domyślna to pierwszy obraz przycisku ( `CMenuImages::IdArrowDown`).

### <a name="remarks"></a>Uwagi

##  <a name="settextcolor"></a>CMFCButton::SetTextColor

Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczony.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parametry

*clrText*<br/>
podczas Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Ustawia kolor tekstu przycisku dla wybranego przycisku.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parametry

*clrTextHot*<br/>
podczas Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

##  <a name="settooltip"></a>CMFCButton:: SetToolTip — etykietka narzędzia

Kojarzy etykietkę narzędzia z przyciskiem.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parametry

*lpszToolTipText*<br/>
podczas Wskaźnik na tekst etykietki narzędzia. Określ wartość NULL, aby wyłączyć etykietkę narzędzia.

### <a name="remarks"></a>Uwagi

##  <a name="sizetocontent"></a>CMFCButton::SizeToContent

Zmienia rozmiar przycisku, aby zawierał jego tekst i obraz przycisku.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
podczas Wartość TRUE, aby obliczyć, ale nie zmieniać, nowy rozmiar przycisku; Wartość FALSE, aby zmienić rozmiar przycisku. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

`CSize` Obiekt, który zawiera nowy rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda oblicza nowy rozmiar, który obejmuje poziomy margines 10 pikseli i pionowy margines 5 pikseli.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[Klasa CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)
