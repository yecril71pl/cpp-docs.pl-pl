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
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505321"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Klasa CMFCDropDownToolbarButton

Typ przycisku paska narzędzi, który zachowuje się jak zwykły przycisk po kliknięciu. Jednak otwiera pasek narzędzi listy rozwijanej ( [Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) , jeśli użytkownik naciśnie przycisk, a następnie połączy pasek narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Konstruuje `CMFCDropDownToolbarButton` obiekt.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|[CMFCDropDownToolbarButton::D ropDownToolbar](#dropdowntoolbar)|Otwiera pasek narzędzi listy rozwijanej.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopiuje tekst z przycisku paska narzędzi do menu. (Przesłania [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Pobiera pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.|
|`CMFCDropDownToolbarButton::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCDropDownToolbarButton:: IsDropDown](#isdropdown)|Określa, czy pasek narzędzi listy rozwijanej jest aktualnie otwarty.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Określa, czy przycisk może być wyświetlany z rozszerzonym obramowaniem. (Przesłania [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Wywoływane przez platformę, by obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Przesłania [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Wywoływane przez platformę, aby obsłużyć komunikat [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) . (Przesłania `CMCToolBarButton::OnCancelMode`).|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi. (Przesłania [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton:: onkliknięcia](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton:: onkliknięciu](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy. (Przesłania [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_HELPHITTEST. (Przesłania [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modyfikuje udostępnione menu, gdy aplikacja wyświetli menu skrótów na nadrzędnym pasku narzędzi. (Przesłania [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton:: OnDraw](#ondraw)|Wywoływane przez platformę, by narysować przycisk przy użyciu określonych stylów i opcji. (Przesłania [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wywoływane przez platformę, aby narysować przycisk w okienku **polecenia** okna dialogowego **Dostosowywanie** . (Przesłania [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton:: serializować](#serialize)|Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum. (Przesłania [CMFCToolBarButton:: serializować](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Ustawia domyślne polecenie, które jest używane przez platformę, gdy użytkownik kliknie przycisk.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Określa czas, przez który użytkownik musi trzymać przycisk myszy w dół przed wyświetleniem paska narzędzi listy rozwijanej.|

## <a name="remarks"></a>Uwagi

`CMFCDropDownToolBarButton` Różni się od zwykłego przycisku w tym, że ma małą strzałkę w prawym dolnym rogu przycisku. Gdy użytkownik wybierze przycisk z paska narzędzi listy rozwijanej, struktura wyświetli jego ikonę na przycisku paska narzędzi najwyższego poziomu (przycisk z małą strzałką w prawym dolnym rogu).

Aby uzyskać informacje na temat sposobu implementowania paska narzędzi listy rozwijanej, zobacz [Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Obiekt może zostać wyeksportowany do obiektu [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) i wyświetlany jako przycisk menu z menu podręcznym. `CMFCDropDownToolBarButton`

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar. h

##  <a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Odwołanie do przycisku źródła, z którego ma zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skopiować kolejny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być typu `CMFCDropDownToolbarButton`.

##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Konstruuje `CMFCDropDownToolbarButton` obiekt.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
podczas Domyślny tekst przycisku.

*pToolBar*<br/>
podczas Wskaźnik do `CMFCDropDownToolBar` obiektu, który jest wyświetlany, gdy użytkownik naciśnie przycisk.

### <a name="remarks"></a>Uwagi

Drugie przeciążenie konstruktora jest kopiowane do przycisku rozwijanego pierwszy przycisk z paska narzędzi, który *pToolBar* określa.

Zwykle przycisk paska narzędzi listy rozwijanej używa tekstu z ostatnio używanego przycisku na pasku narzędzi, który *pToolBar* określa. Używa tekstu określonego przez *lpszName* , gdy przycisk jest konwertowany do przycisku menu lub jest wyświetlany na karcie **polecenia** okna dialogowego **Dostosowywanie** . Aby uzyskać więcej informacji na temat **dostosowywania** okna dialogowego, zobacz [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCDropDownToolbarButton` klasy. Ten fragment kodu jest częścią [przykładu demonstracyjnego Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::D ropDownToolbar

Otwiera pasek narzędzi listy rozwijanej.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Okno nadrzędne ramki rozwijanej lub wartość NULL, aby użyć okna nadrzędnego przycisku paska narzędzi listy rozwijanej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda [CMFCDropDownToolbarButton:: onkliknięciu](#onclick) wywołuje tę metodę, aby otworzyć pasek narzędzi listy rozwijanej, gdy użytkownik naciśnie przycisk, a następnie przytrzyma pasek narzędzi.

Te metody tworzą pasek narzędzi listy rozwijanej przy użyciu metody [CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create) . Jeśli nadrzędny pasek narzędzi jest zadokowany w pionie, ta metoda umieszcza pasek narzędzi listy rozwijanej do lewej lub prawej strony nadrzędnego paska narzędzi, w zależności od dopasowania. W przeciwnym razie ta metoda umieszcza pasek narzędzi listy rozwijanej pod nadrzędnym paskiem narzędzi.

Ta metoda kończy się niepowodzeniem, jeśli *pWnd* ma wartość null, a przycisk paska narzędzi listy rozwijanej nie ma okna nadrzędnego.

##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Kopiuje tekst z przycisku paska narzędzi do menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
podczas Odwołanie do przycisku menu docelowego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje implementację klasy bazowej ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), a następnie dołącza do docelowego przycisku menu w menu podręcznym zawierającym każdy element menu paska narzędzi na tym przycisku. Ta metoda nie dołącza podmenu do menu podręcznego.

Ta metoda kończy się niepowodzeniem, jeśli `m_pToolBar`nadrzędny pasek narzędzi,, ma wartość null lub Implementacja klasy bazowej zwraca wartość false.

##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Pobiera pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Wartość zwracana

Pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca `m_pToolBar` element członkowski danych.

##  <a name="isdropdown"></a>CMFCDropDownToolbarButton:: IsDropDown

Określa, czy pasek narzędzi listy rozwijanej jest aktualnie otwarty.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli pasek narzędzi listy rozwijanej jest aktualnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura otwiera pasek narzędzi listy rozwijanej przy użyciu metody [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) . Struktura zamyka pasek narzędzi listy rozwijanej, gdy użytkownik naciśnie przycisk myszy z lewej strony w nieklienckim obszarze paska narzędzi listy rozwijanej.

##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Określa, czy przycisk może być wyświetlany z rozszerzonym obramowaniem.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przycisk paska narzędzi może być wyświetlany z rozszerzoną krawędzią; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o rozszerzonych obramowaniu, zobacz [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Określa czas, przez który użytkownik musi trzymać przycisk myszy w dół przed wyświetleniem paska narzędzi listy rozwijanej.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Uwagi

Czas opóźnienia jest mierzony w milisekundach. Wartość domyślna to 500. Możesz ustawić inne opóźnienie, zmieniając wartość tego udostępnionego elementu członkowskiego danych.

##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Wywoływane przez platformę, by obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*sizeDefault*<br/>
podczas Domyślny rozmiar przycisku.

*bHorz*<br/>
podczas Stan dokowania nadrzędnego paska narzędzi. Ten parametr ma wartość TRUE, jeśli pasek narzędzi jest zadokowany w poziomie lub jest przenoszony lub FAŁSZ, jeśli pasek narzędzi jest zadokowany w pionie.

### <a name="return-value"></a>Wartość zwracana

`SIZE` Struktura, która zawiera wymiary przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) przez dodanie szerokości strzałki listy rozwijanej do poziomego wymiaru przycisku.

##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Nowe okno nadrzędne.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) przez wyczyszczenie etykiety tekstowej ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) i ustawienie [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) i [CMFCToolBarButton :: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) elementy członkowskie danych na wartość false.

##  <a name="onclick"></a>CMFCDropDownToolbarButton:: onkliknięcia

Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Okno nadrzędne przycisku paska narzędzi.

*bDelay*<br/>
podczas Ma wartość TRUE, jeśli komunikat powinien być obsłużony z opóźnieniem.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej, [CMFCToolBarButton:: onkliknięcia](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizując stan paska narzędzi listy rozwijanej.

Gdy użytkownik kliknie przycisk paska narzędzi, ta metoda tworzy czasomierz, który czeka na czas określony przez element członkowski danych [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay) , a następnie otwiera pasek narzędzi listy rozwijanej przy użyciu [CMFCDropDownToolbarButton ::D Metoda ropDownToolbar](#dropdowntoolbar) . Ta metoda zamyka pasek narzędzi listy rozwijanej, gdy użytkownik kliknie przycisk paska narzędzi.

##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej, [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizując stan paska narzędzi listy rozwijanej.

Ta metoda przerywa czasomierz paska narzędzi listy rozwijanej, jeśli jest aktywny. Gdy jest otwarty, zamyka pasek narzędzi listy rozwijanej.

Aby uzyskać więcej informacji na temat paska narzędzi listy rozwijanej i czasomierza paska narzędzi listy rozwijanej, zobacz [CMFCDropDownToolbarButton:: onkliknięciu](#onclick).

##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Okno nadrzędne przycisku paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przycisk przetwarza komunikat pomocy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) przez wywołanie metody [CMFCDropDownToolbarButton:: onkliknięciu](#onclick) z parametrem *BDELAY* ustawionym na wartość false. Ta metoda zwraca wartość, która jest zwracana przez [CMFCDropDownToolbarButton:: onkliknięciu](#onclick).

Aby uzyskać więcej informacji o komunikacie WM_HELPHITTEST, [Zobacz TN028: Obsługa](../../mfc/tn028-context-sensitive-help-support.md)pomocy kontekstowej.

##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Modyfikuje udostępnione menu, gdy aplikacja wyświetli menu skrótów na nadrzędnym pasku narzędzi.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
podczas Menu do dostosowania.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) przez wyłączenie następujących elementów menu:

- **Kopiuj obraz przycisku**

- **Wygląd przycisku**

- **Obraz**

- **Text**

- **Obraz i tekst**

Zastąp tę metodę, aby zmodyfikować menu skrótów, które jest wyświetlane przez strukturę w trybie dostosowywania.

##  <a name="ondraw"></a>CMFCDropDownToolbarButton:: OnDraw

Wywoływane przez platformę, by narysować przycisk przy użyciu określonych stylów i opcji.

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

*pDC*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*cinania*<br/>
podczas Prostokąt ograniczający przycisku.

*pImages*<br/>
podczas Kolekcja obrazów pasków narzędzi skojarzonych z przyciskiem.

*bHorz*<br/>
podczas Stan dokowania nadrzędnego paska narzędzi. Ten parametr ma wartość TRUE, jeśli przycisk jest zadokowany w poziomie i FAŁSZ, gdy przycisk jest zadokowany w pionie.

*bCustomizeMode*<br/>
podczas Określa, czy pasek narzędzi jest w trybie dostosowywania. Ten parametr ma wartość TRUE, jeśli pasek narzędzi jest w trybie dostosowywania i ma wartość FAŁSZ, jeśli pasek narzędzi nie jest w trybie dostosowywania.

*bHighlight*<br/>
podczas Określa, czy przycisk jest wyróżniony. Ten parametr ma wartość TRUE, jeśli przycisk jest wyróżniony i ma wartość FALSE, gdy przycisk nie jest wyróżniony.

*bDrawBorder*<br/>
podczas Określa, czy przycisk ma wyświetlać jego obramowanie. Ten parametr ma wartość TRUE, gdy przycisk powinien wyświetlać jego obramowanie i FAŁSZ, gdy przycisk nie powinien wyświetlać jego obramowania.

*bGrayDisabledButtons*<br/>
podczas Określa, czy wyłączać wyłączone przyciski, czy użyć kolekcji disabled images. Ten parametr ma wartość TRUE, jeśli przyciski wyłączone powinny być cieniowane i FAŁSZ, gdy ta metoda powinna używać kolekcji disabled images.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dostosować rysowanie przycisków paska narzędzi.

##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Wywoływane przez platformę, aby narysować przycisk w okienku **polecenia** okna dialogowego **Dostosowywanie** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*cinania*<br/>
podczas Prostokąt ograniczający przycisku.

*bSelected*<br/>
podczas Określa, czy przycisk jest wybrany. Jeśli ten parametr ma wartość TRUE, przycisk jest zaznaczony. Jeśli ten parametr ma wartość FALSE, przycisk nie jest zaznaczony.

### <a name="return-value"></a>Wartość zwracana

Szerokość przycisku w określonym kontekście urządzenia (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez okno dialogowe dostosowywania (karta **polecenia** ), gdy przycisk jest wymagany do wyświetlania siebie w polu listy rozwijanej przez właściciela.

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) przez zmianę etykiety tekstowej przycisku na nazwę przycisku (czyli do wartości parametru *lpszName* , który został przesłany do konstruktora ).

##  <a name="serialize"></a>CMFCDropDownToolbarButton:: serializować

Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
podczas `CArchive` Obiekt, z którego lub do serializacji.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: serializować](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) przez Serializowanie identyfikatora zasobu nadrzędnego paska narzędzi. Podczas ładowania archiwum ( [CArchive::](../../mfc/reference/carchive-class.md#isloading) IsLoading zwraca wartość różną od zera) Ta metoda ustawia `m_pToolBar` element członkowski danych na pasek narzędzi zawierający serializowany identyfikator zasobu.

##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Ustawia domyślne polecenie, które jest używane przez platformę, gdy użytkownik kliknie przycisk.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia domyślnego.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić domyślne polecenie, które jest wykonywane przez tę platformę, gdy użytkownik kliknie przycisk. Element o IDENTYFIKATORze polecenia określony przez *uiCmd* musi znajdować się na liście rozwijanej nadrzędnego paska narzędzi.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
