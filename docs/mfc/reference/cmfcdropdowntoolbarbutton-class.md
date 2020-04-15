---
title: Klasa CMFCDropDownToolbarButton
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: d62d5ecb0962f74a5dac1658c207cfb08cf12588
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367607"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Klasa CMFCDropDownToolbarButton

Typ przycisku paska narzędzi, który zachowuje się jak zwykły przycisk po kliknięciu. Jednak otwiera rozwijany pasek narzędzi ( [CMFCDropDownToolBar Class,](../../mfc/reference/cmfcdropdowntoolbar-class.md) jeśli użytkownik naciśnie i przytrzymuje przycisk paska narzędzi w dół.

## <a name="syntax"></a>Składnia

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Konstruuje `CMFCDropDownToolbarButton` obiekt.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Zastępuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otwiera rozwijany pasek narzędzi.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopiuje tekst z przycisku paska narzędzi do menu. (Zastępuje [przycisk CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Pobiera rozwijany pasek narzędzi skojarzony z przyciskiem.|
|`CMFCDropDownToolbarButton::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Określa, czy rozwijany pasek narzędzi jest aktualnie otwarty.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Określa, czy przycisk może być wyświetlany z rozszerzonym obramowaniem. (Zastępuje [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Wywoływana przez strukturę, aby obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Zastępuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Wywoływana przez platformę do obsługi [komunikatu WM_CANCELMODE.](/windows/win32/winmsg/wm-cancelmode) (Przesłania `CMCToolBarButton::OnCancelMode`).|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Zastępuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Wywoływana przez strukturę, gdy użytkownik kliknie przycisk myszy. (Zastępuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Wywoływane przez strukturę, gdy użytkownik zwalnia przycisk myszy. (Zastępuje [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_HELPHITTEST. (Zastępuje [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modyfikuje podane menu, gdy aplikacja wyświetla menu skrótów na nadrzędnym pasku narzędzi. (Zastępuje [przycisk CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Wywoływane przez strukturę, aby narysować przycisk przy użyciu określonych stylów i opcji. (Zastępuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wywoływane przez strukturę, aby narysować przycisk w okienku **Polecenia** okna dialogowego **Dostosowywanie.** (Zastępuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum. (Zastępuje [przycisk CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Ustawia domyślne polecenie używane przez platformę, gdy użytkownik kliknie przycisk.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Określa czas, przez który użytkownik musi przytrzymać przycisk myszy przed wyświetleniem rozwijanego paska narzędzi.|

## <a name="remarks"></a>Uwagi

A `CMFCDropDownToolBarButton` różni się od zwykłego przycisku tym, że ma małą strzałkę w prawym dolnym rogu przycisku. Po wybraniu przez użytkownika przycisku z rozwijanego paska narzędzi, struktura wyświetla swoją ikonę na przycisku paska narzędzi najwyższego poziomu (przycisk z małą strzałką w prawym dolnym rogu).

Aby uzyskać informacje dotyczące sposobu implementacji rozwijanego paska narzędzi, zobacz [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Obiekt `CMFCDropDownToolBarButton` może być eksportowany do obiektu [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) i wyświetlany jako przycisk menu z wyskakującym menu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Odwołanie do przycisku źródłowego, z którego mają być kopiowane.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być `CMFCDropDownToolbarButton`typu .

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Konstruuje `CMFCDropDownToolbarButton` obiekt.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
[w] Domyślny tekst przycisku.

*pToolBar (pToolBar)*<br/>
[w] Wskaźnik do `CMFCDropDownToolBar` obiektu, który jest wyświetlany po naciśnięciu przycisku przez użytkownika.

### <a name="remarks"></a>Uwagi

Drugie przeciążenie konstruktora kopiuje do przycisku rozwijanego pierwszy przycisk z paska narzędzi, który określa *pToolBar.*

Zazwyczaj przycisk rozwijanego paska narzędzi używa tekstu z ostatnio używanego przycisku na pasku narzędzi, który określa *pToolBar.* Używa tekstu określonego przez *lpszName,* gdy przycisk jest konwertowany na przycisk menu lub jest wyświetlany na karcie **Polecenia** okna dialogowego **Dostosowywanie.** Aby uzyskać więcej informacji na temat okna dialogowego **Dostosowywanie,** zobacz [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCDropDownToolbarButton` skonstruować obiekt klasy. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar

Otwiera rozwijany pasek narzędzi.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Okno nadrzędne ramki rozwijanej lub NULL do używania okna nadrzędnego przycisku paska narzędzi rozwijanego.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[CMFCDropDownToolbarButton::OnClick](#onclick) metoda wywołuje tę metodę, aby otworzyć pasek narzędzi rozwijanych, gdy użytkownik naciska i przytrzymuje przycisk paska narzędzi w dół.

Ta metoda tworzy pasek narzędzi listy rozwijanej przy użyciu [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) metody. Jeśli nadrzędny pasek narzędzi jest zadokowany w pionie, ta metoda umieszcza pasek narzędzi rozwijany po lewej lub prawej stronie nadrzędnego paska narzędzi, w zależności od dopasowania. W przeciwnym razie ta metoda umieszcza rozwijany pasek narzędzi pod nadrzędnym paskiem narzędzi.

Ta metoda kończy się niepowodzeniem, jeśli *pWnd* ma wartość NULL, a przycisk rozwijanego paska narzędzi nie ma okna nadrzędnego.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Kopiuje tekst z przycisku paska narzędzi do menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[w] Odwołanie do przycisku menu docelowego.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda powiedzie się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje implementacji klasy podstawowej [(CMFCToolBarButton::ExportToMenuButton),](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)a następnie dołącza do przycisku menu docelowego menu podręcznego, który zawiera każdy element menu paska narzędzi w tym przycisku. Ta metoda nie dołącza podmenu do menu podręcznego.

Ta metoda kończy się niepowodzeniem, jeśli nadrzędny pasek narzędzi , `m_pToolBar`ma wartość NULL lub implementacja klasy podstawowej zwraca wartość FAŁSZ.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Pobiera rozwijany pasek narzędzi skojarzony z przyciskiem.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozwijany pasek narzędzi skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Ta metoda `m_pToolBar` zwraca element członkowski danych.

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

Określa, czy rozwijany pasek narzędzi jest aktualnie otwarty.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli rozwijany pasek narzędzi jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura otwiera pasek narzędzi rozwijanych przy użyciu [CMFCDropDownToolbutton::DropDownToolbar](#dropdowntoolbar) metody. Struktura zamyka pasek narzędzi rozwijanych, gdy użytkownik naciśnie lewy przycisk myszy w obszarze nie-klient rozwijanego paska narzędzi.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Określa, czy przycisk może być wyświetlany z rozszerzonym obramowaniem.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk paska narzędzi może być wyświetlany z rozszerzonym obramowaniem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat rozszerzonych obramowań, zobacz [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Określa czas, przez który użytkownik musi przytrzymać przycisk myszy przed wyświetleniem rozwijanego paska narzędzi.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Uwagi

Czas opóźnienia jest mierzony w milisekundach. Wartość domyślna to 500. Można ustawić kolejne opóźnienie, zmieniając wartość tego udostępnionego elementu członkowskiego danych.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Wywoływana przez strukturę, aby obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*rozmiarDefault*<br/>
[w] Domyślny rozmiar przycisku.

*Bhorz*<br/>
[w] Stan dokującej nadrzędnego paska narzędzi. Ten parametr ma wartość PRAWDA, jeśli pasek narzędzi jest zadokowany poziomo lub jest przestawny, lub FALSE, jeśli pasek narzędzi jest zadokowany w pionie.

### <a name="return-value"></a>Wartość zwracana

Struktura `SIZE` zawierająca wymiary przycisku w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) przez dodanie szerokości strzałki rozwijanej do wymiaru poziomego rozmiaru przycisku.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Nowe okno nadrzędne.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) przez wyczyszczenie etykiety tekstowej ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) i ustawienie [CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) i [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) elementów członkowskich danych na FALSE.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFCDropDownToolbarButton::OnClick

Wywoływana przez strukturę, gdy użytkownik kliknie przycisk myszy.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Okno nadrzędne przycisku paska narzędzi.

*bDelay (własówce)*<br/>
[w] PRAWDA, jeśli wiadomość powinna być obsługiwana z opóźnieniem.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy [podstawowej, CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizując stan paska narzędzi rozwijanych.

Gdy użytkownik kliknie przycisk paska narzędzi, ta metoda tworzy czasomierz, który czeka czas określony przez [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) element członkowski danych, a następnie otwiera rozwijany pasek narzędzi przy użyciu [CMFCDropDownToolButton::DropDownToolbar](#dropdowntoolbar) metody. Ta metoda zamyka pasek narzędzi rozwijanych po raz drugi użytkownik kliknie przycisk paska narzędzi.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Wywoływane przez strukturę, gdy użytkownik zwalnia przycisk myszy.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizując stan paska narzędzi rozwijanych.

Ta metoda zatrzymuje czasomierz rozwijany paska narzędzi, jeśli jest aktywny. Zamyka rozwijany pasek narzędzi, jeśli jest otwarty.

Aby uzyskać więcej informacji na temat rozwijanego paska narzędzi i czasu na pasku narzędzi rozwijanego, zobacz [CMFCDropDownToolbarButton::OnClick](#onclick).

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Okno nadrzędne przycisku paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk przetwarza komunikat pomocy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) przez wywołanie [CMFCDropDownToolbarButton::OnClick](#onclick) metody z *bDelay* ustawiony na FALSE. Ta metoda zwraca wartość zwracaną przez [CMFCDropDownToolbarButton::OnClick](#onclick).

Aby uzyskać więcej informacji na temat komunikatu WM_HELPHITTEST, zobacz [TN028: Pomoc kontekstowa](../../mfc/tn028-context-sensitive-help-support.md).

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Modyfikuje podane menu, gdy aplikacja wyświetla menu skrótów na nadrzędnym pasku narzędzi.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[w] Menu do dostosowania.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy podstawowej ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)), wyłączając następujące elementy menu:

- **Obraz przycisku Kopiowania**

- **Wygląd przycisku**

- **Image (Obraz)**

- **Tekst**

- **Obraz i tekst**

Zastąd w tej metodzie należy zmodyfikować menu skrótów wyświetlane w trybie dostosowywania.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw

Wywoływane przez strukturę, aby narysować przycisk przy użyciu określonych stylów i opcji.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku.

*pImages (Zdjęcia)*<br/>
[w] Kolekcja obrazów paska narzędzi skojarzonych z przyciskiem.

*Bhorz*<br/>
[w] Stan dokującej nadrzędnego paska narzędzi. Ten parametr ma wartość PRAWDA, gdy przycisk jest zadokowany poziomo i FALSE, gdy przycisk jest zadokowany w pionie.

*b Tryb dokuczowania*<br/>
[w] Określa, czy pasek narzędzi jest w trybie dostosowywania. Ten parametr ma wartość TRUE, gdy pasek narzędzi jest w trybie dostosowywania i FALSE, gdy pasek narzędzi nie jest w trybie dostosowywania.

*bWyświetlenie*<br/>
[w] Określa, czy przycisk jest wyróżniony. Ten parametr ma wartość PRAWDA, gdy przycisk jest podświetlony i FALSE, gdy przycisk nie jest podświetlony.

*bDrawBorder*<br/>
[w] Określa, czy przycisk ma być wyświetlany w obramowanie. Ten parametr ma wartość PRAWDA, gdy przycisk powinien wyświetlać obramowanie i FAŁSZ, gdy przycisk nie powinien wyświetlać obramowania.

*bGrayDisabledButtons*<br/>
[w] Określa, czy przyciski wyłączone mają być cieniowane, czy używane do korzystania z kolekcji obrazów wyłączonych. Ten parametr ma wartość PRAWDA, gdy wyłączone przyciski powinny być cieniowane i FALSE, gdy ta metoda powinna używać kolekcji wyłączonych obrazów.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dostosować rysowanie przycisków paska narzędzi.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Wywoływane przez strukturę, aby narysować przycisk w okienku **Polecenia** okna dialogowego **Dostosowywanie.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku.

*bWybrany*<br/>
[w] Czy wybrano przycisk. Jeśli ten parametr ma wartość PRAWDA, zostanie wybrany przycisk. Jeśli ten parametr ma wartość FAŁSZ, przycisk nie jest zaznaczony.

### <a name="return-value"></a>Wartość zwracana

Szerokość przycisku w określonym kontekście urządzenia w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez okno dialogowe dostosowywania (karta **Polecenia),** gdy przycisk jest wymagany do wyświetlenia się w polu listy rysowania właściciela.

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) zmieniając etykietę tekstową przycisku na nazwę przycisku (czyli do wartości *parametru lpszName,* który został przekazany do konstruktora).

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFCDropDownToolbarButton::Serialize

Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
[w] Obiekt, `CArchive` z którego lub do którego serialize.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) przez serializacji identyfikator zasobu nadrzędnego paska narzędzi. Podczas ładowania archiwum ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) zwraca wartość niezerową), ta metoda ustawia element członkowski `m_pToolBar` danych na pasku narzędzi, który zawiera identyfikator zasobu szeregowego.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Ustawia domyślne polecenie używane przez platformę, gdy użytkownik kliknie przycisk.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia domyślnego.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić domyślne polecenie, które wykonuje framework, gdy użytkownik kliknie przycisk. Element o identyfikatorze polecenia określonym przez *uiCmd* musi znajdować się na nadrzędnym pasku narzędzi.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
