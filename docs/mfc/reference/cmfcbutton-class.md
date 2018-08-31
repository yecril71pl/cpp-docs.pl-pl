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
ms.openlocfilehash: 155aa704efe0686fc03be6e2b12c076656fad7a1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217512"
---
# <a name="cmfcbutton-class"></a>Klasa CMFCButton
`CMFCButton` Klasa dodaje funkcjonalność do [CButton](../../mfc/reference/cbutton-class.md) klasy, takie jak wyrównanie tekstu przycisku, łączenie przycisku tekstu i obrazu, wybierając kursor i określając etykietkę narzędzia.  
  
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
|[CMFCButton::CleanUp](#cleanup)|Resetuje wewnętrznych zmiennych i zwalnia przydzielone zasoby, takie jak obrazy, bitmap i ikon.|  
|`CMFCButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCButton::DrawItem`|Wywoływane przez platformę, gdy zmieni się wizualny aspekt przycisku rysowanych przez właściciela została zmieniona. (Przesłania [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Określa, czy ma być wyświetlany pełny tekst etykietki narzędzia w oknie duża etykietka narzędzia lub skrócona wersja tekstu w oknie małych etykietki narzędzia.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Określa czcionkę tekstu przycisku, jest taka sama jak czcionki menu aplikacji.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Określa, czy styl obramowania przycisku odnosi się do bieżącego motywu Windows.|  
|`CMFCButton::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Zwraca odwołanie do podstawowej kontrolki tooltip.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Wskazuje, czy pole wyboru lub przycisku radiowego jest przycisku automatycznego.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Wskazuje, czy przycisk jest ustawiany w trybie auto-repeat.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Wskazuje, czy przycisk to przycisk pola wyboru.|  
|[CMFCButton::IsChecked](#ischecked)|Wskazuje, czy bieżący przycisk jest zaznaczony.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Wskazuje, czy przycisk jest wyróżniona.|  
|[CMFCButton::IsPressed](#ispressed)|Wskazuje, czy przycisk jest wypychane i wyróżnione.|  
|[CMFCButton::IsPushed](#ispushed)|Wskazuje, czy przycisk zostanie przypisany.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Wskazuje, czy przycisk to przycisk radiowy.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Wskazuje, czy styl obramowania przycisku odnosi się do bieżącego motywu Windows.|  
|`CMFCButton::OnDrawParentBackground`|Rysuje tło elementu nadrzędnego przycisku w podanym obszarze. (Przesłania [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Ustawia tryb auto-repeat przycisku.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Ustawia obraz dla przycisku zaznaczone.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Ustawia kolor tła tekstu przycisku.|  
|[CMFCButton::SetImage](#setimage)|Ustawia obraz dla przycisku.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Ustawia obraz kursora.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Ustawia kursor do obrazu dłoni.|  
|[CMFCButton::SetStdImage](#setstdimage)|Używa `CMenuImages` obiekt do ustawiania obrazu przycisku.|  
|[CMFCButton::SetTextColor](#settextcolor)|Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczone.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Ustawia kolor tekstu przycisku dla przycisku, który jest wybrany.|  
|[CMFCButton::SetTooltip](#settooltip)|Kojarzy etykietka narzędzia z przyciskiem.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku, aby zawierać jego przycisku tekstu i obrazów.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować przycisku.|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|Metoda wywoływana przez platformę, by narysować obramowanie przycisku.|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Metoda wywoływana przez platformę, by narysować prostokąt fokusu na przycisku.|  
|[CMFCButton::OnDrawText](#ondrawtext)|Metoda wywoływana przez platformę, by narysować tekst przycisku.|  
|[CMFCButton::OnFillBackground](#onfillbackground)|Metoda wywoływana przez platformę, by narysować tła tekstu przycisku.|  
|[CMFCButton::SelectFont](#selectfont)|Pobiera czcionki, który jest skojarzony z kontekstem określonego urządzenia.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Wskazuje, czy należy narysować prostokąt fokusu wokół przycisku.|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Wskazuje, czy do wyróżnienia BS_CHECKBOX styl przycisku, gdy kursor znajduje się nad nią.|  
|[CMFCButton::m_bRightImage](#m_brightimage)|Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.|  
|[CMFCButton::m_bTransparent](#m_btransparent)|Wskazuje, czy przycisk jest przezroczysty.|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Określa wyrównanie tekstu przycisku.|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Określa styl przycisku, takie jak bez obramowania, płaskiego, ta stosowana jest stała i 3D.|  
  
## <a name="remarks"></a>Uwagi  
 Inne rodzaje przyciski są uzyskiwane z `CMFCButton` klasy, takie jak [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) klasy, która obsługuje hiperłącza, i `CMFCColorButton` klasy, która obsługuje okno dialogowe próbnika kolorów.  
  
 Styl `CMFCButton` obiekt może być *3D*, *prostego*, *rozdzielana płaskiej* lub *bez obramowania*. Po lewej stronie, do góry lub do środka przycisku można wyrównać tekst przycisku. W czasie wykonywania można kontrolować, czy przycisk powoduje wyświetlenie tekstu, obrazów i obrazów. Można również określić, czy obraz określonego kursor wyświetlany gdy kursor znajduje się nad przyciskiem.  
  
 Tworzenie formantu przycisku, bezpośrednio w kodzie lub za pomocą **Kreator klas MFC** narzędzia i szablonu okna dialogowego. Jeśli bezpośrednio tworzyć kontrolki przycisku Dodaj `CMFCButton` zmiennej do aplikacji, a następnie wywołania konstruktora i `Create` metody `CMFCButton` obiektu. Jeśli używasz **Kreator klas MFC**, Dodaj `CButton` zmiennej do swojej aplikacji, a następnie zmień typ zmiennej z `CButton` do `CMFCButton`.  
  
 Do obsługi komunikatów powiadomień w aplikacji okno dialogowe, należy dodać wpis mapy komunikatów i program obsługi zdarzeń dla każdego powiadomienia. Powiadomienia wysyłane przez `CMFCButton` obiektu są takie same, jak wysyłane przez `CButton` obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować właściwości przycisku przy użyciu różnych metod w `CMFCButton` klasy. Przykład jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
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
 Resetuje wewnętrznych zmiennych i zwalnia przydzielone zasoby, takie jak obrazy, bitmap i ikon.  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip  
 Określa, czy ma być wyświetlany pełny tekst etykietki narzędzia w oknie duża etykietka narzędzia lub skrócona wersja tekstu w oknie małych etykietki narzędzia.  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bOn*  
 Wartość TRUE, aby wyświetlić wszystkie tekstu. Wartość FAŁSZ, aby tekst wyświetlany obcięte.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 Określa czcionkę tekstu przycisku, jest taka sama jak czcionki menu aplikacji.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bOn*  
 Wartość TRUE, aby użyć czcionki menu aplikacji jako czcionki tekstu przycisku; Użyj czcionki systemowej jest FALSE. Wartość domyślna to TRUE.  
  
 [in] *bRedraw*  
 Wartość TRUE, aby natychmiast odświeżyć ekran; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda nie umożliwia określenia czcionki tekstu przycisku, można określić czcionki z [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) metody. Jeśli nie określisz czcionkę w ogóle, struktura Ustawia czcionkę domyślną.  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 Określa, czy styl obramowania przycisku odnosi się do bieżącego motywu Windows.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bWłączenie*  
 Wartość TRUE, aby użyć bieżącego motywu Windows do rysowania obramowań przycisk; Wartość FALSE, aby nie używać motyw Windows. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ma wpływ na wszystkie przyciski do aplikacji, które są uzyskiwane z `CMFCButton` klasy.  
  
##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl  
 Zwraca odwołanie do podstawowej kontrolki tooltip.  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do podstawowej kontrolki tooltip.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck  
 Wskazuje, czy pole wyboru lub przycisku radiowego jest przycisku automatycznego.  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli styl przycisku BS_AUTOCHECKBOX lub BS_AUTORADIOBUTTON; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 Wskazuje, czy przycisk jest ustawiany w trybie auto-repeat.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest ustawiany w trybie auto-repeat; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCButton::SetAutorepeatMode](#setautorepeatmode) metodę, aby ustawić przycisku na tryb automatyczny repeat.  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 Wskazuje, czy przycisk to przycisk pola wyboru.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk BS_CHECKBOX lub BS_AUTOCHECKBOX styl; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 Wskazuje, czy bieżący przycisk jest zaznaczony.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zaznaczono opcję bieżącego przycisku; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Struktura używa różnych sposobów, aby wskazać, że różne rodzaje przyciski są zaznaczone. Na przykład przycisku radiowego jest zaznaczone, gdy zawiera on kropka; pole wyboru jest zaznaczone, gdy zawiera on **X**.  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 Wskazuje, czy przycisk jest wyróżniona.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest wyróżniony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk staje się wyróżniona, gdy wskaźnik myszy znajdzie się nad przyciskiem.  
  
##  <a name="ispressed"></a>  CMFCButton::IsPressed  
 Wskazuje, czy przycisk jest wypychane i wyróżnione.  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest wciśnięty; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ispushed"></a>  CMFCButton::IsPushed  
 Wskazuje, czy przycisk zostanie przypisany.  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk jest równoznaczne z wypchnięciem; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 Wskazuje, czy przycisk to przycisk radiowy.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli jest to styl przycisku BS_RADIOBUTTON lub BS_AUTORADIOBUTTON; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 Wskazuje, czy styl obramowania przycisku odnosi się do bieżącego motywu Windows.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli styl obramowania przycisku odnosi się do bieżącego motywu Windows. w przeciwnym razie wartość FALSE.  
  
##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 Wskazuje, czy należy narysować prostokąt fokusu wokół przycisku.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bDrawFocus` elementu członkowskiego na wartość TRUE, aby określić, że struktura będzie narysować prostokąt fokusu wokół tekstu przycisku i obrazów, jeśli przycisk zostanie ustawiony fokus.  
  
 `CMFCButton` Konstruktor inicjuje tą składową, aby wartość TRUE.  
  
##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 Wskazuje, czy do wyróżnienia BS_CHECKBOX styl przycisku, gdy kursor znajduje się nad nią.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bHighlightChecked` elementu członkowskiego na wartość TRUE, aby określić, w ramach spowoduje wyróżnienie przycisku styl BS_CHECKBOX gdy mysz zatrzyma na niej.  
  
##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 Wskazuje, czy ma być wyświetlany obraz po prawej stronie przycisku.  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bRightImage` elementu członkowskiego na wartość TRUE, aby określić, w ramach spowoduje wyświetlenie obrazu na przycisku z prawej strony etykiety tekstu przycisku.  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 Wskazuje, czy przycisk jest przezroczysty.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw `m_bTransparent` elementu członkowskiego na wartość TRUE, aby określić, że struktura spowoduje, że przycisk Przezroczysty. `CMFCButton` Konstruktor inicjuje tą składową, aby wartość FALSE.  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 Określa wyrównanie tekstu przycisku.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj jednej z następujących `CMFCButton::AlignStyle` wartości wyliczenia, aby określić wyrównanie tekstu przycisku:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|ALIGN_CENTER|(Ustawienie domyślne) Wyrównanie tekstu przycisku do środka przycisku.|  
|ALIGN_LEFT|Wyrównanie tekstu przycisku po lewej stronie przycisku.|  
|ALIGN_RIGHT|Wyrównuje tekst przycisku po prawej stronie przycisku.|  
  
 `CMFCButton` Konstruktor inicjuje tą składową, aby ALIGN_CENTER.  
  
##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 Określa styl przycisku, takie jak bez obramowania, płaskiego, ta stosowana jest stała i 3D.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono `CMFCButton::m_nFlatStyle` wartości wyliczenia, które określają wygląd przycisku.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Ustawienie domyślne) Przycisk wydaje się mieć wysoki, trójwymiarowej stron. Po kliknięciu przycisku naciśnięcia do głębokiego wcięcia pojawi się przycisk.|  
|BUTTONSTYLE_FLAT|Gdy wskaźnik myszy nie jest wstrzymywane na przycisku, przycisk wydaje się być dwuwymiarowej i nie ma boki zostaje zgłoszone. Gdy mysz nad przyciskiem, ma niski, trójwymiarowej strony pojawi się przycisk. Po kliknięciu przycisku naciśnięcia w płytka wcięcia pojawi się przycisk.|  
|BUTTONSTYLE_SEMIFLAT|Przycisk jest zapewnienie boki niski, trójwymiarowej. Po kliknięciu przycisku naciśnięcia do głębokiego wcięcia pojawi się przycisk.|  
|BUTTONSTYLE_NOBORDERS|Przycisk nie rozwiążemy zgłoszonego problemu stron i jest zawsze wyświetlany dwuwymiarową. Nie ma przycisku naciśnięcia do wcięcia, po kliknięciu.|  
  
 `CMFCButton` Konstruktor inicjuje tą składową, aby BUTTONSTYLE_3D.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób ustawiania wartości `m_nFlatStyle` zmiennej składowej w `CMFCButton` klasy. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>  CMFCButton::OnDraw  
 Metoda wywoływana przez platformę, by narysować przycisku.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Odwołanie do prostokąt, który granic przycisku.  
  
 [in] *uiState*  
 Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` członkiem [struktura DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby użyć własnego kodu do rysowania przycisku.  
  
##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder  
 Metoda wywoływana przez platformę, by narysować obramowanie przycisku.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rectClient*  
 Odwołanie do prostokąt, który granic przycisku.  
  
 [in] *uiState*  
 Bieżący stan przycisku. Aby uzyskać więcej informacji, zobacz `itemState` członkiem [struktura DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) tematu.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby użyć własnego kodu do rysowania obramowania.  
  
##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect  
 Metoda wywoływana przez platformę, by narysować prostokąt fokusu na przycisku.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rectClient*  
 Odwołanie do prostokąt, który granic przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby narysować prostokąt fokusu przy użyciu własnego kodu.  
  
##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText  
 Metoda wywoływana przez platformę, by narysować tekst przycisku.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Odwołanie do prostokąt, który granic przycisku.  
  
 [in] *strText*  
 Tekst do rysowania.  
  
 [in] *uiDTFlags*  
 Flagi, które określają sposób formatowania tekstu. Aby uzyskać więcej informacji, zobacz *nFormat* parametru [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) metody.  
  
 [in] *uiState*  
 (Zastrzeżone).  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby użyć własnego kodu do rysowania tekstu przycisku.  
  
##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground  
 Metoda wywoływana przez platformę, by narysować tła tekstu przycisku.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rectClient*  
 Odwołanie do prostokąt, który granic przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby użyć własnego kodu do rysowania tła przycisku.  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 Pobiera czcionki, który jest skojarzony z kontekstem określonego urządzenia.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
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
 [in] *nTimeDelay*  
 Nieujemna liczba, która określa odstęp między wiadomości, które są wysyłane do okna nadrzędnego. Interwał jest mierzony w milisekundach, a jego wartość domyślna to 500 milisekund. Określ wartości zero spowoduje wyłączenie trybu auto-repeat wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że przycisk stale wysyłaj wm_command — komunikaty do okna nadrzędnego, aż przycisk zostanie zwolniony, lub *nTimeDelay* parametr ma wartość zero.  
  
##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage  
 Ustawia obraz dla przycisku zaznaczone.  
  
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
 [in] *hIcon*  
 Obsługa na ikonę, która zawiera mapę bitową i maska dla nowego obrazu.  
  
 [in] *bAutoDestroy*  
 Wartość TRUE, aby określić zasoby mapy bitowej niszczone automatycznie. w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
 [in] *hIconHot*  
 Uchwyt ikony, który zawiera obraz dla wybranego stanu.  
  
 [in] *hBitmap*  
 Dojście do mapy bitowej, który zawiera obraz stanu niezaznaczone.  
  
 [in] *hBitmapHot*  
 Dojście do mapy bitowej, który zawiera obraz dla wybranego stanu.  
  
 [in] *bMap3dColors*  
 Określa przezroczysty kolor tła przycisku; oznacza to, że powierzchnia przycisku. Wartość TRUE, aby użyć wartości kolorów RGB (192 192, 192); Wartość FALSE, aby użyć wartości kolorów zdefiniowanych przez `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *uiBmpResId*  
 Identyfikator zasobu obrazu niezaznaczone.  
  
 [in] *uiBmpHotResId*  
 Identyfikator zasobu dla wybranego obrazu.  
  
 [in] *hIconDisabled*  
 Obsługa do ikony symbolizującej wyłączone obrazu.  
  
 [in] *hBitmapDisabled*  
 Dojście do mapy bitowej, który zawiera obraz wyłączone.  
  
 [in] *uiBmpDsblResID*  
 Identyfikator zasobu mapy bitowej wyłączone.  
  
 [in] *bAlphaBlend*  
 Wartość true, używaj tylko 32-bitowych obrazów używających kanał alfa. Wartość FALSE, aby nie używać kanał alfa tylko obrazy. Wartość domyślna to FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 Ustawia kolor tła tekstu przycisku.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *crFace*  
 Wartość koloru RGB.  
  
 [in] *bRedraw*  
 Wartość TRUE, aby od razu; wyświetlanie zawartości ekranu w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia definiowanie nowych kolor wypełnienia tła przycisku (twarzy). Należy zauważyć, że w tle nie jest wypełniony, kiedy [CMFCButton::m_bTransparent](#m_btransparent) zmiennej składowej ma wartość TRUE.  
  
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
 [in] *hIcon*  
 Obsługa na ikonę, która zawiera mapę bitową i maska dla nowego obrazu.  
  
 [in] *bAutoDestroy*  
 Wartość TRUE, aby określić zasoby mapy bitowej niszczone automatycznie. w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
 [in] *hIconHot*  
 Uchwyt ikony, który zawiera obraz dla wybranego stanu.  
  
 [in] *hBitmap*  
 Dojście do mapy bitowej, który zawiera obraz stanu niezaznaczone.  
  
 [in] *hBitmapHot*  
 Dojście do mapy bitowej, który zawiera obraz dla wybranego stanu.  
  
 [in] *uiBmpResId*  
 Identyfikator zasobu obrazu niezaznaczone.  
  
 [in] *uiBmpHotResId*  
 Identyfikator zasobu dla wybranego obrazu.  
  
 [in] *bMap3dColors*  
 Określa przezroczysty kolor tła przycisku; oznacza to, że powierzchnia przycisku. Wartość TRUE, aby użyć wartości kolorów RGB (192 192, 192); Wartość FALSE, aby użyć wartości kolorów zdefiniowanych przez `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *hIconDisabled*  
 Obsługa do ikony symbolizującej wyłączone obrazu.  
  
 [in] *hBitmapDisabled*  
 Dojście do mapy bitowej, który zawiera obraz wyłączone.  
  
 [in] *uiBmpDsblResID*  
 Identyfikator zasobu mapy bitowej wyłączone.  
  
 [in] *bAlphaBlend*  
 Wartość true, używaj tylko 32-bitowych obrazów używających kanał alfa. Wartość FALSE, aby nie używać kanał alfa tylko obrazy. Wartość domyślna to FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia różnych wersjach `SetImage` method in Class metoda `CMFCButton` klasy. Przykład jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 Ustawia obraz kursora.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hcursor*  
 Uchwyt kursora.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia kojarzenie obraz do kursora, takich jak kursor ręcznie przy użyciu przycisku. Kursor jest ładowany z zasobów aplikacji.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia `SetMouseCursor` method in Class metoda `CMFCButton` klasy. Przykład jest częścią kodu w [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 Ustawia kursor do obrazu dłoni.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia kojarzenie obraz kursora dłoni z przyciskiem. Kursor jest ładowany z zasobów aplikacji.  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 Używa `CMenuImages` obiekt do ustawiania obrazu przycisku.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *identyfikator*  
 Jeden z identyfikatorów obrazu przycisku, które jest zdefiniowane w `CMenuImage::IMAGES_IDS` wyliczenia. Obrazy, takie jak strzałki, numery PIN i przycisków radiowych określonych wartości obrazu.  
  
 [in] *stanu*  
 Jeden z identyfikatorów stan obrazu przycisku, które jest zdefiniowane w `CMenuImages::IMAGE_STATE` wyliczenia. Stany obraz określ przycisk kolorów, takich jak czarny, szary, jasny szary, biały i ciemny szary. Wartość domyślna to `CMenuImages::ImageBlack`.  
  
 [in] *idDisabled*  
 Jeden z identyfikatorów obrazu przycisku, które jest zdefiniowane w `CMenuImage::IMAGES_IDS` wyliczenia. Obraz, który wskazuje, czy przycisk jest wyłączony. Wartość domyślna to pierwsze obraz przycisku ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 Ustawia kolor tekstu przycisku dla przycisku, który nie jest zaznaczone.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrText*  
 Wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 Ustawia kolor tekstu przycisku dla przycisku, który jest wybrany.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrTextHot*  
 Wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 Kojarzy etykietka narzędzia z przyciskiem.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszToolTipText*  
 Wskaźnik do tekst etykietki narzędzia. Należy określić wartość NULL, aby wyłączyć etykietki narzędzia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 Zmienia rozmiar przycisku, aby zawierać jego przycisku tekstu i obrazów.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bCalcOnly*  
 Wartość TRUE, aby obliczyć, ale nie na zmienianie nowy rozmiar przycisku; Wartość FALSE, aby zmienić rozmiar przycisku. Wartość domyślna to FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który zawiera nowy rozmiar przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda oblicza nowy rozmiar, zawierający poziomy margines 10 pikseli i pionowego marginesu 5 pikseli.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)   
 [Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)   
 [Klasa CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)
