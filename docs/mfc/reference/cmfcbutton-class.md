---
title: Klasa CMFCButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73a3bb877bec385a9f7e56191286c9b560da8610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378829"
---
# <a name="cmfcbutton-class"></a>Klasa CMFCButton
`CMFCButton` Klasa dodaje funkcjonalność do [CButton](../../mfc/reference/cbutton-class.md) klasy, takie jak wyrównanie tekstu przycisku, łączenie przycisk tekstowych i obrazów, wybierając kursora i określanie etykietka narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|Domyślny konstruktor.|  
|`CMFCButton::~CMFCButton`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|Resetuje wewnętrzne zmienne i zwalnia przydzielone zasoby, takie jak obrazy, mapy bitowe i ikon.|  
|`CMFCButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCButton::DrawItem`|Wywoływane przez platformę, gdy zmieniono visual aspekt przycisku rysowanych przez właściciela. (Przesłania [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Określa, czy mają być wyświetlane w oknie tooltip dużych lub skrócona wersja tekstu w oknie małych tooltip pełny tekst etykietki narzędzia.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Określa czcionkę tekstu przycisku jest taka sama jak czcionki menu aplikacji.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Określa, czy styl obramowania przycisku odnosi się do bieżącego motywu systemu Windows.|  
|`CMFCButton::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Zwraca odwołanie do podstawowej formantu tooltip.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Wskazuje, czy pole wyboru lub przycisku radiowego jest przycisk Automatyczny.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Wskazuje, czy przycisk jest ustawiony na tryb automatyczny repeat.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Wskazuje, czy przycisk to przycisk pola wyboru.|  
|[CMFCButton::IsChecked](#ischecked)|Wskazuje, czy bieżący przycisk jest zaznaczony.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Wskazuje, czy przycisk jest podświetlona.|  
|[CMFCButton::IsPressed](#ispressed)|Wskazuje, czy przycisk jest naciśnięty i wyróżnione.|  
|[CMFCButton::IsPushed](#ispushed)|Wskazuje, czy przycisk jest naciśnięty.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Wskazuje, czy przycisk to przycisk radiowy.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Wskazuje, czy styl obramowania przycisku odnosi się do bieżącego motywu systemu Windows.|  
|`CMFCButton::OnDrawParentBackground`|Rysuje tła elementu nadrzędnego przycisku w określonym obszarze. (Przesłania [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Ustawia tryb auto-repeat przycisku.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Ustawia obraz dla przycisku zaznaczenia.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Ustawia kolor tła tekstu przycisku.|  
|[CMFCButton::SetImage](#setimage)|Ustawia obraz dla przycisku.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Ustawia obraz kursora.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Ustawia kursor do obrazu dłoni.|  
|[CMFCButton::SetStdImage](#setstdimage)|Używa `CMenuImages` obiektu w celu ustawienia obrazu przycisku.|  
|[CMFCButton::SetTextColor](#settextcolor)|Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczone.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Ustawia kolor tekstu przycisku dla przycisku, który jest zaznaczone.|  
|[CMFCButton::SetTooltip](#settooltip)|Kojarzy etykietka narzędzia z przyciskiem.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku zawierają tekst przycisku i obrazu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować przycisku.|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|Wywoływane przez platformę, by narysować obramowanie przycisku.|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę, by narysować prostokąt fokusu dla przycisku.|  
|[CMFCButton::OnDrawText](#ondrawtext)|Wywoływane przez platformę, by narysować tekstu przycisku.|  
|[CMFCButton::OnFillBackground](#onfillbackground)|Wywoływane przez platformę, by narysować tła tekstu przycisku.|  
|[CMFCButton::SelectFont](#selectfont)|Pobiera czcionki, która jest skojarzona z kontekstem określonego urządzenia.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Wskazuje, czy Rysuj prostokąt fokusu wokół przycisku.|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Wskazuje, czy wyróżnić bs_checkbox — styl przycisku, gdy kursor znajduje się nad nim.|  
|[CMFCButton::m_bRightImage](#m_brightimage)|Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.|  
|[CMFCButton::m_bTransparent](#m_btransparent)|Wskazuje, czy przycisk jest przezroczysty.|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Określa wyrównanie tekstu przycisku.|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Określa styl przycisku, takich jak bez obramowania, płaski, częściowo płaskiego lub 3W.|  
  
## <a name="remarks"></a>Uwagi  
 Inne rodzaje przycisków pochodzą od `CMFCButton` klas, takich jak [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) klasy, która obsługuje hiperłącza, i `CMFCColorButton` klasy, która obsługuje okno dialogowe selektora kolorów.  
  
 Styl `CMFCButton` obiekt może być *3D*, *płaskiej*, *częściowo płaski* lub *obramowanie*. Tekst przycisku można wyrównać na lewo, top lub Centrum przycisku. W czasie wykonywania można kontrolować, czy przycisk wyświetla tekstu, obrazów i obrazu. Można również określić, czy obraz określonego kursor wyświetlany gdy kursor znajduje się nad przyciskiem.  
  
 Tworzenie formantu przycisku bezpośrednio w kodzie, lub za pomocą **Kreator klas MFC** narzędzie i szablon okno dialogowe. W przypadku utworzenia kontrolkę przycisku bezpośrednio dodać `CMFCButton` zmienną do aplikacji, a następnie wywołania konstruktora i `Create` metody `CMFCButton` obiektu. Jeśli używasz **Kreator klas MFC**, Dodaj `CButton` zmienną do aplikacji, a następnie zmień typ zmiennej z `CButton` do `CMFCButton`.  
  
 Do obsługi komunikatów powiadomień w aplikacji okno dialogowe, Dodaj wpis mapy wiadomości i program obsługi zdarzeń dla każdego powiadomienia. Powiadomienia wysyłane przez `CMFCButton` obiektu są takie same jak wysyłane przez `CButton` obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skonfigurować właściwości przycisku przy użyciu różnych metod w `CMFCButton` klasy. Przykładem jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
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
 **Nagłówek:** afxbutton.h  
  
##  <a name="cleanup"></a>  CMFCButton::CleanUp  
 Resetuje wewnętrzne zmienne i zwalnia przydzielone zasoby, takie jak obrazy, mapy bitowe i ikon.  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip  
 Określa, czy mają być wyświetlane w oknie tooltip dużych lub skrócona wersja tekstu w oknie małych tooltip pełny tekst etykietki narzędzia.  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bOn`  
 `TRUE` Aby wyświetlić cały tekst; `FALSE` do tekstu wyświetlanego obcięte.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 Określa czcionkę tekstu przycisku jest taka sama jak czcionki menu aplikacji.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bOn`  
 `TRUE` Aby używać menu aplikacji jako czcionki tekstu przycisku; `FALSE` do użycia czcionki systemowej. Wartość domyślna to `TRUE`.  
  
 [in] `bRedraw`  
 `TRUE` Aby natychmiast odświeżyć ekran; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda nie umożliwia określenie czcionki tekstu przycisku, można określić czcionkę z [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) metody. Jeśli nie określisz czcionkę w ogóle, platformę ustawia domyślną czcionkę.  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 Określa, czy styl obramowania przycisku odnosi się do bieżącego motywu systemu Windows.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bEnable`  
 `TRUE` Aby użyć bieżącego motywu systemu Windows do rysowania obramowań przycisk; `FALSE` nie korzystać z kompozycji systemu Windows. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ma wpływ na wszystkie przyciski do aplikacji, które pochodzą od `CMFCButton` klasy.  
  
##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl  
 Zwraca odwołanie do podstawowej formantu tooltip.  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do podstawowej formantu tooltip.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck  
 Wskazuje, czy pole wyboru lub przycisku radiowego jest przycisk Automatyczny.  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli przycisk ma styl bs_autocheckbox — albo bs_autoradiobutton —; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 Wskazuje, czy przycisk jest ustawiony na tryb automatyczny repeat.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest ustawiony na tryb automatyczny repeat; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCButton::SetAutorepeatMode](#setautorepeatmode) metodę, aby ustawić tryb auto-repeat przycisku.  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 Wskazuje, czy przycisk to przycisk pola wyboru.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisku bs_checkbox — lub bs_autocheckbox — styl; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 Wskazuje, czy bieżący przycisk jest zaznaczony.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli bieżący przycisk jest zaznaczony; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa różne sposoby, aby wskazać, że zaznaczone są różnego rodzaju przycisków. Na przykład przycisku radiowego jest sprawdzana podczas zawiera kropkę; pole wyboru jest zaznaczone, gdy zawiera **X**.  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 Wskazuje, czy przycisk jest podświetlona.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zostanie wyróżniona przycisku; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk zostanie podświetlona, gdy mysz znajduje się nad przyciskiem.  
  
##  <a name="ispressed"></a>  CMFCButton::IsPressed  
 Wskazuje, czy przycisk jest naciśnięty i wyróżnione.  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest naciśnięty; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ispushed"></a>  CMFCButton::IsPushed  
 Wskazuje, czy przycisk jest naciśnięty.  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest naciśnięty; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 Wskazuje, czy przycisk to przycisk radiowy.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli styl przycisku jest bs_radiobutton — lub bs_autoradiobutton —; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 Wskazuje, czy styl obramowania przycisku odnosi się do bieżącego motywu systemu Windows.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli styl obramowania przycisku odnosi się do bieżącego motywu systemu Windows. w przeciwnym razie `FALSE`.  
  
##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 Wskazuje, czy Rysuj prostokąt fokusu wokół przycisku.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bDrawFocus` członka `TRUE` Aby określić, czy platformę będzie Rysuj prostokąt fokusu wokół tekstu przycisku i obrazu, jeśli przycisku uzyskuje fokus.  
  
 `CMFCButton` Konstruktor inicjuje ten element członkowski do `TRUE`.  
  
##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 Wskazuje, czy wyróżnić bs_checkbox — styl przycisku, gdy kursor znajduje się nad nim.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bHighlightChecked` członka `TRUE` do określenia, czy platformę wyróżnione przycisku bs_checkbox — styl podczas przesuwania wskaźnika myszy nad nim.  
  
##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bRightImage` członka `TRUE` do określenia, że platformę będzie wyświetlać obrazu przycisku po prawej stronie przycisku tekst etykiety.  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 Wskazuje, czy przycisk jest przezroczysty.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bTransparent` członka `TRUE` do określenia, że platformę dokona przycisk Przezroczysty. `CMFCButton` Konstruktor inicjuje ten element członkowski do `FALSE`.  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 Określa wyrównanie tekstu przycisku.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj jednej z następujących `CMFCButton::AlignStyle` wartości wyliczenia, aby określić wyrównania tekstu przycisku:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|ALIGN_CENTER|(Ustawienie domyślne) Wyrównanie tekstu przycisku do Centrum przycisku.|  
|ALIGN_LEFT|Wyrównanie tekstu przycisku po lewej stronie przycisku.|  
|ALIGN_RIGHT|Wyrównanie tekstu przycisku z prawej strony przycisku.|  
  
 `CMFCButton` Konstruktor inicjuje ten element członkowski do ALIGN_CENTER.  
  
##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 Określa styl przycisku, takich jak bez obramowania, płaski, częściowo płaskiego lub 3W.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono `CMFCButton::m_nFlatStyle` wartości wyliczenia, które określają wygląd przycisku.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Ustawienie domyślne) Przycisk jest mają wysoki, trójwymiarowy strony. Po kliknięciu przycisku przycisku wydaje się zostać naciśnięte do dokładnego wcięcia.|  
|BUTTONSTYLE_FLAT|Gdy wskaźnik myszy nie wstrzymana na przycisku, przycisk wydaje się być dwuwymiarowa i nie ma zgłoszono strony. Gdy wskaźnik myszy zostanie wstrzymana na przycisku, przycisk jest mają niska, trójwymiarowy strony. Po kliknięciu przycisku przycisku wydaje się zostać naciśnięte do skrócona wcięcia.|  
|BUTTONSTYLE_SEMIFLAT|Przycisk jest mają niska, trójwymiarowy strony. Po kliknięciu przycisku przycisku wydaje się zostać naciśnięte do dokładnego wcięcia.|  
|BUTTONSTYLE_NOBORDERS|Przycisk nie zgłosiły stronach i zawsze jest wyświetlany dwuwymiarową. Przycisk nie naciśnięto do wcięcia, po kliknięciu.|  
  
 `CMFCButton` Konstruktor inicjuje ten element członkowski do `BUTTONSTYLE_3D`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób ustawiania wartości `m_nFlatStyle` zmiennej członkowskiej w `CMFCButton` klasy. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>  CMFCButton::OnDraw  
 Wywoływane przez platformę, by narysować przycisku.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rect`  
 Odwołanie do prostokąt zakresem przycisku.  
  
 [in] `uiState`  
 Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` członkiem [struktura DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby użyć własnego kodu do rysowania przycisku.  
  
##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder  
 Wywoływane przez platformę, by narysować obramowanie przycisku.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rectClient`  
 Odwołanie do prostokąt zakresem przycisku.  
  
 [in] `uiState`  
 Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` członkiem [struktura DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, aby użyć własnego kodu, aby narysować obramowanie.  
  
##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect  
 Wywoływane przez platformę, by narysować prostokąt fokusu dla przycisku.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rectClient`  
 Odwołanie do prostokąt zakresem przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, za pomocą własnego kodu Rysuj prostokąt fokusu.  
  
##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText  
 Wywoływane przez platformę, by narysować tekstu przycisku.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rect`  
 Odwołanie do prostokąt zakresem przycisku.  
  
 [in] `strText`  
 Tekst do rysowania.  
  
 [in] `uiDTFlags`  
 Flagi, które określają sposób formatowania tekstu. Aby uzyskać więcej informacji, zobacz `nFormat` parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metody.  
  
 [in] `uiState`  
 (Zastrzeżone).  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę do użycia z własnego kodu ma zostać narysowany tekst przycisku.  
  
##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground  
 Wywoływane przez platformę, by narysować tła tekstu przycisku.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rectClient`  
 Odwołanie do prostokąt zakresem przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę do własnych kod do rysowania tła przycisku.  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 Pobiera czcionki, która jest skojarzona z kontekstem określonego urządzenia.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zastępuje tę metodę, aby pobrać czcionkę przy użyciu własnego kodu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode  
 Ustawia tryb auto-repeat przycisku.  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nTimeDelay`  
 Nieujemna liczba, która określa interwał między wiadomości, które są wysyłane do okna nadrzędnego. Interwał jest mierzony w milisekundach i jego wartość domyślna to 500 milisekund. Określ wartości zero spowoduje wyłączenie trybu auto-repeat wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że przycisk stale wysyłaj WM_COMMAND — komunikaty do okna nadrzędnego, aż zwolnieniu przycisku lub `nTimeDelay` parametr ma wartość zero.  
  
##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage  
 Ustawia obraz dla przycisku zaznaczenia.  
  
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
 [in] `hIcon`  
 Dojście do ikony, która zawiera mapę bitową i maska dla nowego obrazu.  
  
 [in] `bAutoDestroy`  
 `TRUE` Aby określić zasoby mapy bitowej niszczone automatycznie; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
 [in] `hIconHot`  
 Dojście do ikony, która zawiera obraz dla wybranego stanu.  
  
 [in] `hBitmap`  
 Dojście do mapy bitowej, który zawiera obraz stanu niezaznaczone.  
  
 [in] `hBitmapHot`  
 Dojście do mapy bitowej zawierającego obraz dla wybranego stanu.  
  
 [in] `bMap3dColors`  
 Określa przezroczysty kolor tła przycisku; oznacza to, powierzchni przycisku. `TRUE` Aby użyć wartości kolorów RGB (192, 192, 192); `FALSE` Aby użyć wartości kolorów zdefiniowanych przez `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] `uiBmpResId`  
 Identyfikator zasobu obrazu niezaznaczone.  
  
 [in] `uiBmpHotResId`  
 Identyfikator zasobu dla wybranego obrazu.  
  
 [in] `hIconDisabled`  
 Dojście do ikony dla wyłączonego obrazu.  
  
 [in] `hBitmapDisabled`  
 Dojście do mapy bitowej, który zawiera wyłączenia obraz.  
  
 [in] `uiBmpDsblResID`  
 Identyfikator zasobu mapy bitowej wyłączone.  
  
 [in] `bAlphaBlend`  
 `TRUE` Aby użyć tylko obrazy 32-bitowych używających kanał alfa. `FALSE`, aby nie używać tylko obrazy kanału alfa. Wartość domyślna to `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 Ustawia kolor tła tekstu przycisku.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `crFace`  
 Wartości kolorów RGB.  
  
 [in] `bRedraw`  
 `TRUE` Aby odświeżyć ekran natychmiast; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zdefiniować nowy kolor wypełnienia tła przycisku (krój). Należy pamiętać, że tło nie jest wypełniony, kiedy [CMFCButton::m_bTransparent](#m_btransparent) zmiennej członkowskiej jest `TRUE`.  
  
##  <a name="setimage"></a>  CMFCButton::SetImage  
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
 [in] `hIcon`  
 Dojście do ikony, która zawiera mapę bitową i maska dla nowego obrazu.  
  
 [in] `bAutoDestroy`  
 `TRUE` Aby określić zasoby mapy bitowej niszczone automatycznie; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
 [in] `hIconHot`  
 Dojście do ikony, która zawiera obraz dla wybranego stanu.  
  
 [in] `hBitmap`  
 Dojście do mapy bitowej, który zawiera obraz stanu niezaznaczone.  
  
 [in] `hBitmapHot`  
 Dojście do mapy bitowej zawierającego obraz dla wybranego stanu.  
  
 [in] `uiBmpResId`  
 Identyfikator zasobu obrazu niezaznaczone.  
  
 [in] `uiBmpHotResId`  
 Identyfikator zasobu dla wybranego obrazu.  
  
 [in] `bMap3dColors`  
 Określa przezroczysty kolor tła przycisku; oznacza to, powierzchni przycisku. `TRUE` Aby użyć wartości kolorów RGB (192, 192, 192); `FALSE` Aby użyć wartości kolorów zdefiniowanych przez `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] `hIconDisabled`  
 Dojście do ikony dla wyłączonego obrazu.  
  
 [in] `hBitmapDisabled`  
 Dojście do mapy bitowej, który zawiera wyłączenia obraz.  
  
 [in] `uiBmpDsblResID`  
 Identyfikator zasobu mapy bitowej wyłączone.  
  
 [in] `bAlphaBlend`  
 `TRUE` Aby użyć tylko obrazy 32-bitowych używających kanał alfa. `FALSE`, aby nie używać tylko obrazy kanału alfa. Wartość domyślna to `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych wersjach `SetImage` metoda `CMFCButton` klasy. Przykładem jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 Ustawia obraz kursora.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `hcursor`  
 Dojście kursora.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby skojarzyć obrazem kursora, takich jak kursora ręcznie przy użyciu przycisku. Kursor jest ładowany z zasobów aplikacji.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `SetMouseCursor` metoda `CMFCButton` klasy. Przykładem jest częścią kodu w [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 Ustawia kursor do obrazu dłoni.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby skojarzyć obrazu kursora strony dłoni z przyciskiem. Kursor jest ładowany z zasobów aplikacji.  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 Używa `CMenuImages` obiektu w celu ustawienia obrazu przycisku.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `id`  
 Jeden z identyfikatorów obrazu przycisku zdefiniowanych w `CMenuImage::IMAGES_IDS` wyliczenia. Wartości obrazu Określ obrazy, takie jak strzałki, numery PIN i przycisków radiowych.  
  
 [in] `state`  
 Jeden z identyfikatorów stan obrazu przycisku zdefiniowanych w `CMenuImages::IMAGE_STATE` wyliczenia. Stany obrazu Określ przycisk kolorów, takich jak czarny, szary, światła szary, biały i ciemny szary. Wartość domyślna to `CMenuImages::ImageBlack`.  
  
 [in] `idDisabled`  
 Jeden z identyfikatorów obrazu przycisku zdefiniowanych w `CMenuImage::IMAGES_IDS` wyliczenia. Obraz wskazuje, czy przycisk jest wyłączona. Wartość domyślna to pierwszy obraz przycisku ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczone.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `clrText`  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 Ustawia kolor tekstu przycisku dla przycisku, który jest zaznaczone.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `clrTextHot`  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 Kojarzy etykietka narzędzia z przyciskiem.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszToolTipText`  
 Wskaźnik do tekst etykietki narzędzia. Określ wartość NULL, aby wyłączyć etykietka narzędzia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 Zmienia rozmiar przycisku zawierają tekst przycisku i obrazu.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bCalcOnly`  
 `TRUE` Aby obliczyć, ale nie można zmieniać nowy rozmiar przycisku; `FALSE` Aby zmienić rozmiar przycisku. Wartość domyślna to `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który zawiera nowy rozmiar przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda oblicza nowy rozmiar poziomy margines 10 pikseli i pionowego marginesu 5 pikseli.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)   
 [Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)   
 [Klasa CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)
