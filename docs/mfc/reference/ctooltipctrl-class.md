---
title: Klasa CToolTipCtrl
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: 53a5a5b6871680f9758d140174dcceae6c53f568
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752197"
---
# <a name="ctooltipctrl-class"></a>Klasa CToolTipCtrl

Hermetyzuje funkcjonalność "kontrolki narzędzia", małego okna podręcznego, w którym jest wyświetlany pojedynczy wiersz tekstu opisujący cel narzędzia w aplikacji.

## <a name="syntax"></a>Składnia

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Konstruuje `CToolTipCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolTipCtrl::Aktywuj](#activate)|Aktywuje i dezaktywuje kontrolkę końcówki narzędzia.|
|[CToolTipCtrl::AddTool](#addtool)|Rejestruje narzędzie za pomocą kontrolki etykietki narzędzia.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Konwertuje między prostokątem wyświetlania tekstu formantu narzędzia a jego prostokątem okna.|
|[CToolTipCtrl::Utwórz](#create)|Tworzy kontrolkę narzędzia i dołącza `CToolTipCtrl` ją do obiektu.|
|[CToolTipCtrl::CreateEx](#createex)|Tworzy kontrolkę etykietki narzędzia z określonymi stylami `CToolTipCtrl` rozszerzonymi systemu Windows i dołącza ją do obiektu.|
|[CToolTipCtrl::DelTool](#deltool)|Usuwa narzędzie z kontrolki narzędzia.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Pobiera rozmiar końcówki narzędzia.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Pobiera informacje, takie jak rozmiar, położenie i tekst okna etykietki narzędzia, które wyświetla bieżąca etykietka narzędzia.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Pobiera początkowe, wyskakujące okienka i ponownie pokazuje czas trwania, które są obecnie ustawione dla kontrolki narzędzia.|
|[CToolTipCtrl::GetMargin](#getmargin)|Pobiera górny, lewy, dolny i prawy margines ustawiony dla okna etykietki narzędzia.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Pobiera maksymalną szerokość okna końcówki narzędzia.|
|[CToolTipCtrl::GetText](#gettext)|Pobiera tekst, który formant etykietki narzędzia utrzymuje dla narzędzia.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Pobiera kolor tła w oknie etykietki narzędzia.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Pobiera kolor tekstu w oknie etykietki narzędzia.|
|[CToolTipCtrl::GetTitle](#gettitle)|Pobiera tytuł bieżącej kontrolki etykietki narzędzia.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Pobiera liczbę narzędzi obsługiwanych przez kontrolkę narzędzia.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Pobiera informacje, które kontrola etykietki narzędzia przechowuje na temat narzędzia.|
|[CToolTipCtrl::HitTest](#hittest)|Testuje punkt, aby ustalić, czy znajduje się w prostokątze ograniczającym danego narzędzia. Jeśli tak, pobiera informacje o narzędziu.|
|[CToolTipCtrl::Pop](#pop)|Usuwa z widoku wyświetlane okno końcówki narzędzia.|
|[CToolTipCtrl::Popup](#popup)|Powoduje, że bieżąca etykietka narzędzia ma być wyświetlana we współrzędnych ostatniego komunikatu myszy.|
|[CToolTipCtrl::RelayEvent](#relayevent)|Przekazuje komunikat myszy do formantu etykietki narzędzia w celu przetworzenia.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Ustawia początkowe, wyskakujące okienka i ponownie pokazuje czas trwania formantu etykietki narzędzia.|
|[CToolTipCtrl::SetMargin](#setmargin)|Ustawia górny, lewy, dolny i prawy margines okna etykietki narzędzia.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Ustawia maksymalną szerokość okna końcówki narzędzia.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Ustawia kolor tła w oknie etykietki narzędzia.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Ustawia kolor tekstu w oknie etykietki narzędzia.|
|[CToolTipCtrl::SetTitle](#settitle)|Dodaje standardową ikonę i ciąg tytułu do etykietki narzędzia.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Ustawia informacje, które etykietka narzędzia przechowuje dla narzędzia.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Ustawia nowy prostokąt ograniczający dla narzędzia.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny okna etykietki narzędzia.|
|[CToolTipCtrl::Aktualizacja](#update)|Wymusza ponowne wyrycie bieżącego narzędzia.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Ustawia tekst etykietki narzędzia dla narzędzia.|

## <a name="remarks"></a>Uwagi

"Narzędzie" to okno, takie jak okno podrzędne lub formant, albo prostokątny obszar zdefiniowany przez aplikację w obszarze klienta okna. Etykietka narzędzia jest ukryta przez większość czasu, pojawiając się tylko wtedy, gdy użytkownik umieszcza kursor na narzędziu i pozostawia go tam przez około pół sekundy. Etykietka narzędzia pojawi się w pobliżu kursora i zniknie, gdy użytkownik kliknie przycisk myszy lub odsunie kursor od narzędzia.

`CToolTipCtrl`zapewnia funkcję kontrolowania czasu początkowego i czasu trwania końcówki narzędzia, szerokości marginesu otaczającego tekst końcówki narzędzia, szerokość samego okna końcówki narzędzia oraz kolor tła i tekstu końcówki narzędzia. Pojedyncza kontrolka narzędzia może dostarczyć informacji dla więcej niż jednego narzędzia.

Klasa `CToolTipCtrl` zapewnia funkcjonalność kontroli typowej końcówki narzędzia systemu Windows. Ten formant (i `CToolTipCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersjach 3.51 lub nowszych.

Aby uzyskać więcej informacji na temat włączania porad dotyczących narzędzi, zobacz [Porady dotyczące narzędzi w systemie Windows nie pochodzące z programu CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Aby uzyskać więcej `CToolTipCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::Aktywuj

Wywołanie tej funkcji, aby włączyć lub wyłączyć kontrolkę etykietki narzędzia.

```cpp
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktywowanie*<br/>
Określa, czy kontrolka narzędzia ma być aktywowana czy dezaktywowana.

### <a name="remarks"></a>Uwagi

Jeśli *bAktywej jest* PRAWDA, formant jest aktywowany; jeśli FALSE, jest dezaktywowany.

Gdy kontrolka etykietki narzędzia jest aktywna, informacje o etykietce narzędzia są wyświetlane, gdy kursor znajduje się na narzędziu zarejestrowanym w formancie; gdy jest nieaktywny, informacje o etykietce narzędzia nie są wyświetlane, nawet gdy kursor znajduje się na narzędziu.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipCtrl::AddTool

Rejestruje narzędzie za pomocą kontrolki etykietki narzędzia.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nDJtek*<br/>
Identyfikator zasobu ciągu zawierającego tekst narzędzia.

*lpRectTool*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) zawierającej współrzędne prostokąta ograniczającego narzędzia. Współrzędne są względem lewego górnego rogu obszaru klienta okna oznaczonego przez *pWnd*.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

*lpszText (tekst)*<br/>
Wskaźnik do tekstu narzędzia. Jeśli ten parametr zawiera wartość LPSTR_TEXTCALLBACK, TTN_NEEDTEXT komunikatów powiadomień przejdź do nadrzędnego okna, które *pWnd* wskazuje.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametry *lpRectTool* i *nIDTool* muszą być prawidłowe lub jeśli *lpRectTool* ma wartość NULL, *nIDTool* musi wynosić 0.

Kontrolka końcówki narzędzia może być skojarzona z więcej niż jednym narzędziem. Wywołanie tej funkcji, aby zarejestrować narzędzie za pomocą kontrolki narzędzia, tak aby informacje przechowywane w etykietce narzędzia były wyświetlane, gdy kursor znajduje się w narzędziu.

> [!NOTE]
> Nie można ustawić końcówki narzędzia `AddTool`na formant statyczny za pomocą .

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipCtrl::AdjustRect

Konwertuje między prostokątem wyświetlania tekstu formantu narzędzia a jego prostokątem okna.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parametry

*lprc (ł.*<br/>
Wskaźnik do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która zawiera prostokąt okna poradki narzędzia lub prostokąt wyświetlania tekstu.

*bLarger*<br/>
Jeśli TRUE, *lprc* jest używany do określenia prostokąta wyświetlania tekstu i odbiera odpowiedni prostokąt okna. Jeśli FALSE, *lprc* jest używany do określenia prostokąta okna i odbiera odpowiedni prostokąt wyświetlania tekstu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli prostokąt został pomyślnie dostosowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego oblicza prostokąt wyświetlania tekstu formantu narzędzia z prostokąta okna lub prostokąt okna porady narzędzia potrzebny do wyświetlenia określonego prostokąta wyświetlania tekstu.

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::Utwórz

Tworzy kontrolkę narzędzia i dołącza `CToolTipCtrl` ją do obiektu.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Określa okno nadrzędne formantu etykietki `CDialog`narzędzia, zwykle okno . Nie może być null.

*Dwstyle*<br/>
Określa styl formantu etykietki narzędzia. Zobacz **uwagi** sekcji, aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CToolTipCtrl` jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruujesz `CToolTipCtrl` w dwóch krokach. Najpierw wywołać konstruktora `CToolTipCtrl` do konstruowania obiektu, a następnie wywołać, `Create` aby utworzyć kontrolkę narzędzia i dołączyć go do `CToolTipCtrl` obiektu.

Parametrem *dwStyle* może być dowolna kombinacja [stylów okien.](../../mfc/reference/styles-used-by-mfc.md#window-styles) Ponadto kontrolka etykietki narzędzia ma dwa style specyficzne dla klasy: TTS_ALWAYSTIP i TTS_NOPREFIX.

|Styl|Znaczenie|
|-----------|-------------|
|TTS_ALWAYSTIP|Określa, że etykietka narzędzia będzie wyświetlana, gdy kursor znajduje się w narzędziu, niezależnie od tego, czy okno właściciela formantu etykietki narzędzia jest aktywne czy nieaktywne. Bez tego stylu kontrolka narzędzia pojawia się, gdy okno właściciela narzędzia jest aktywne, ale nie wtedy, gdy jest nieaktywne.|
|TTS_NOPREFIX|Ten styl uniemożliwia systemowi usunięcie znaku ampersand (&) z ciągu. Jeśli kontrolka etykietki narzędzia nie ma stylu TTS_NOPREFIX, system automatycznie usuwa znaki i znaki, umożliwiając aplikacji używanie tego samego ciągu, co element menu i jako tekst w formancie etykietki narzędzia.|

Kontrolka etykietki narzędzia ma style WS_POPUP i WS_EX_TOOLWINDOW okna, niezależnie od tego, czy są one określone podczas tworzenia formantu.

Aby utworzyć kontrolkę etykietki narzędzia z rozszerzonymi stylami okien, zadzwoń `Create`do [CToolTipCtrl::CreateEx](#createex) zamiast .

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CToolTipCtrl` skojarzyć go z obiektem.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Dwstyle*<br/>
Określa styl formantu etykietki narzędzia. Zobacz **uwagi** sekcji [Tworzenie, aby](#create) uzyskać więcej informacji.

*dwStyleEx (np.*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie inaczej 0.

### <a name="remarks"></a>Uwagi

Zamiast stosować rozszerzone style systemu Windows określone przez przedmową w stylu rozszerzonym systemu Windows WS_EX_ . **WS_EX_** `CreateEx` `Create`

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl

Konstruuje `CToolTipCtrl` obiekt.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `Create` po skonstruowaniu obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

Usuwa narzędzie określone przez *pWnd* i *nIDTool* z kolekcji narzędzi obsługiwanych przez kontrolkę narzędzia.

```cpp
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize

Pobiera rozmiar końcówki narzędzia.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Wskaźnik do struktury [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) końcówki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Rozmiar końcówki narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool

Pobiera informacje, takie jak rozmiar, położenie i tekst okna etykietki narzędzia wyświetlane przez bieżącą kontrolkę narzędzia.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpToolInfo*|[na zewnątrz] Wskaźnik do struktury [TOOLINFO,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) która odbiera informacje o bieżącym oknie etykietki narzędzia.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli informacje zostały pobrane pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat TTM_GETCURRENTTOOL,](/windows/win32/Controls/ttm-getcurrenttool) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera informacje o bieżącym oknie etykietki narzędzia.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime

Pobiera początkowe, wyskakujące okienka i ponownie pokazuje czas trwania aktualnie ustawiony dla kontrolki narzędzia.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parametry

*dwDuration*<br/>
Flaga określająca, która wartość czasu trwania zostanie pobrana. Ten parametr może być jedną z następujących wartości:

- TTDT_AUTOPOP Pobrać czas, przez który okno końcówki narzędzia pozostaje widoczne, jeśli wskaźnik znajduje się nieruchomo w prostokątze obwiedni narzędzia.

- TTDT_INITIAL Pobrać czas, przez który wskaźnik musi pozostawać nieruchomy w prostokątze obwiedni narzędzia, zanim pojawi się okno etykietki narzędzia.

- TTDT_RESHOW Pobrać czas potrzebny na wyświetlenie kolejnych okien etykietek narzędzi, gdy wskaźnik przechodzi z jednego narzędzia do drugiego.

### <a name="return-value"></a>Wartość zwracana

Określony czas opóźnienia w milisekundach

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipCtrl::GetMargin

Pobiera górny, lewy, dolny i prawy margines ustawiony dla okna etykietki narzędzia.

```cpp
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc (ł.*<br/>
Adres `RECT` struktury, która otrzyma informacje o marginesie. Elementy członkowskie struktury [RECT](/windows/win32/api/windef/ns-windef-rect) nie definiują prostokąta ograniczającego. Na potrzeby tego komunikatu członkowie struktury są interpretowane w następujący sposób:

|Członek|Reprezentacja|
|------------|--------------------|
|`top`|Odległość między górnym obramowaniem a górnym tekstem etykietki narzędzia w pikselach.|
|`left`|Odległość między lewą i lewą krawędzią tekstu końcówki w pikselach.|
|`bottom`|Odległość między dolną krawędzią a dolną krawędzią tekstu końcówki w pikselach.|
|`right`|Odległość między prawym i prawym końcem tekstu końcówki w pikselach.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth

Pobiera maksymalną szerokość okna końcówki narzędzia.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna szerokość okna końcówki narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipCtrl::GetText

Pobiera tekst, który formant etykietki narzędzia utrzymuje dla narzędzia.

```cpp
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Odwołanie do `CString` obiektu, który odbiera tekst narzędzia.

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

### <a name="remarks"></a>Uwagi

Parametry *pWnd* i *nIDTool* identyfikują narzędzie. Jeśli to narzędzie zostało wcześniej zarejestrowane za pomocą formantu etykietki narzędzia za pośrednictwem poprzedniego wywołania, obiekt, do `CToolTipCtrl::AddTool`którego odwołuje się parametr *str,* jest przypisywany tekst narzędzia.

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor

Pobiera kolor tła w oknie etykietki narzędzia.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) reprezentująca kolor tła.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor

Pobiera kolor tekstu w oknie etykietki narzędzia.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) reprezentująca kolor tekstu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::GetTitle

Pobiera tytuł bieżącej kontrolki etykietki narzędzia.

```cpp
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pttgt*|[na zewnątrz] Wskaźnik do [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) struktury, która zawiera informacje o ToolTip kontroli. Gdy ta metoda zwraca, *pszTitle* element członkowski [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) struktury wskazuje tekst tytułu.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [TTM_GETTITLE,](/windows/win32/Controls/ttm-gettitle) który jest opisany w windows SDK.

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::GetToolCount

Pobiera liczbę narzędzi zarejestrowanych za pomocą formantu etykietki narzędzia.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba narzędzi zarejestrowanych za pomocą kontrolki narzędzia.

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo

Pobiera informacje, które kontrola etykietki narzędzia przechowuje na temat narzędzia.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*ToolInfo (NarzędzieInfo)*<br/>
Odwołanie do `TOOLINFO` obiektu, który odbiera tekst narzędzia.

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

I `hwnd` `uId` członków struktury [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) odwołuje *CToolInfo* zidentyfikować narzędzie. Jeśli to narzędzie zostało zarejestrowane za pomocą kontrolki narzędzia za pośrednictwem poprzedniego `AddTool`wywołania, `TOOLINFO` struktura jest wypełniona informacjami o narzędziu.

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipCtrl::HitTest

Testuje punkt, aby ustalić, czy znajduje się w prostokątze ograniczającym danego narzędzia i, jeśli tak, pobrać informacje o narzędziu.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*Pt*<br/>
Wskaźnik do `CPoint` obiektu zawierającego współrzędne punktu, który ma zostać przetestowany.

*lpToolInfo*<br/>
Wskaźnik do struktury [TOOLINFO,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) który zawiera informacje o narzędziu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli punkt określony przez informacje o badaniu trafień znajduje się w prostokątze ograniczającym narzędzia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli ta funkcja zwraca wartość niezerową, struktura wskazywalna przez *lpToolInfo* jest wypełniona informacjami na narzędziu, w którego prostokącie znajduje się punkt.

Struktura `TTHITTESTINFO` jest zdefiniowana w następujący sposób:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Określa uchwyt narzędzia.

- `pt`

   Określa współrzędne punktu, jeśli punkt znajduje się w prostokątze ograniczającym narzędzia.

- `ti`

   Informacje o narzędziu. Aby uzyskać więcej `TOOLINFO` informacji na temat struktury, zobacz [CToolTipCtrl::GetToolInfo](#gettoolinfo).

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

Usuwa z widoku wyświetlane okno końcówki narzędzia.

```cpp
void Pop();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_POP](/windows/win32/Controls/ttm-pop)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::Popup

Powoduje, że bieżąca kontrolka etykietki narzędzia jest wyświetlana we współrzędnych ostatniego komunikatu myszy.

```cpp
void Popup();
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [TTM_POPUP,](/windows/win32/Controls/ttm-popup) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie kodu jest wyświetlane okno etykietki narzędzia.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::RelayEvent

Przekazuje komunikat myszy do formantu etykietki narzędzia w celu przetworzenia.

```cpp
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Wskaźnik do struktury [MSG,](/windows/win32/api/winuser/ns-winuser-msg) która zawiera komunikat do przekazywania.

### <a name="remarks"></a>Uwagi

Kontrola etykietki narzędzia przetwarza tylko następujące komunikaty, `RelayEvent`które są wysyłane do niego przez:

|WM_LBUTTONDOWN|Wm_mousemove|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime

Ustawia czas opóźnienia dla kontrolki narzędzia.

```cpp
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parametry

*nDelay (własówce)*<br/>
Określa nowy czas opóźnienia w milisekundach.

*dwDuration*<br/>
Flaga określająca, która wartość czasu trwania zostanie pobrana. Zobacz [CToolTipCtrl::GetDelayTime](#getdelaytime) opis prawidłowych wartości.

*iTime*<br/>
Określony czas opóźnienia w milisekundach.

### <a name="remarks"></a>Uwagi

Czas opóźnienia to czas, przez który kursor musi pozostawać na narzędziu, zanim pojawi się okno końcówki narzędzia. Domyślny czas opóźnienia wynosi 500 milisekund.

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipCtrl::SetMargin

Ustawia górny, lewy, dolny i prawy margines okna etykietki narzędzia.

```cpp
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parametry

*lprc (ł.*<br/>
Adres struktury `RECT` zawierającej informacje o marginesie, które mają zostać ustawione. Elementy członkowskie `RECT` struktury nie definiują prostokąta ograniczającego. Zobacz [CToolTipCtrl::GetMargin](#getmargin) opis informacji o marginesie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth

Ustawia maksymalną szerokość okna końcówki narzędzia.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parametry

*iWidth ( iWidth )*<br/>
Maksymalna szerokość okna końcówki narzędzia, która ma zostać ustawiona.

### <a name="return-value"></a>Wartość zwracana

Poprzednia maksymalna szerokość końcówki.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor

Ustawia kolor tła w oknie etykietki narzędzia.

```cpp
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Nowy kolor tła.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor

Ustawia kolor tekstu w oknie etykietki narzędzia.

```cpp
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Nowy kolor tekstu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipCtrl::SetTitle

Dodaje standardową ikonę i ciąg tytułu do etykietki narzędzia.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parametry

*uIcon ( uIcon )*<br/>
Zobacz *ikonę* [w TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) w windows SDK.

*lpstrTitle (lpstrTitle)*<br/>
Wskaźnik do ciągu tytułu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo

Ustawia informacje, które etykietka narzędzia przechowuje dla narzędzia.

```cpp
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Wskaźnik do struktury [TOOLINFO,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) który określa informacje do ustawionego.

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipCtrl::SetToolRect

Ustawia nowy prostokąt ograniczający dla narzędzia.

```cpp
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

*Lprect*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) określającej nowy prostokąt ograniczający.

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme

Ustawia styl wizualny okna etykietki narzędzia.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Wskaźnik do ciągu Unicode, który zawiera styl wizualny do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość nie jest używana.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu TTM_SETWINDOWTHEME,](/windows/win32/Controls/ttm-setwindowtheme) zgodnie z opisem w windows SDK.

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::Aktualizacja

Wymusza ponowne wyrycie bieżącego narzędzia.

```cpp
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText

Aktualizuje tekst etykietki narzędzia dla narzędzi tego formantu.

```cpp
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskaźnik do tekstu narzędzia.

*Pwnd*<br/>
Wskaźnik do okna zawierającego narzędzie.

*nIDTool (nIDTool)*<br/>
Identyfikator narzędzia.

*nDJtek*<br/>
Identyfikator zasobu ciągu zawierającego tekst narzędzia.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)
