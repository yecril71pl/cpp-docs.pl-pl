---
title: Klasa CMFCToolBarEditBoxButton
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504729"
---
# <a name="cmfctoolbareditboxbutton-class"></a>Klasa CMFCToolBarEditBoxButton

Przycisk paska narzędzi, który zawiera kontrolkę edycji ( [Klasa CEdit](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Składnia

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Konstruuje `CMFCToolBarEditBoxButton` obiekt.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania. (Przesłania [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetEdit](#createedit)|Tworzy nową kontrolkę Edycja na przycisku.|
|`CMFCToolBarEditBoxButton::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Pobiera tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Pobiera identyfikator zasobu menu skrótów, które jest skojarzone z przyciskiem.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Pobiera prostokąt związany z edycją części przycisku Edytuj pole.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: GetEditBox](#geteditbox)|Zwraca wskaźnik do kontrolki edycji osadzonej na przycisku.|
|[CMFCToolBarEditBoxButton:: GetHwnd](#gethwnd)|Pobiera uchwyt okna skojarzony z przyciskiem paska narzędzi. (Przesłania [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)).|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Pobiera region obszaru klienckiego przycisku, który musi zostać narysowany ponownie. (Przesłania [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku ma być wyświetlane po kliknięciu przycisku przez użytkownika. (Przesłania [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode)|Określa, czy przyciski pola edycji mają styl płaski.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) . (Przesłania [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do okna dialogowego **Dostosowywanie** . (Przesłania [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Wywoływane przez platformę, by obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Przesłania [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi. (Przesłania [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton:: onkliknięcia](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton:: onkliknięciu](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR. (Przesłania [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Wywoływane przez platformę, by narysować przycisk przy użyciu określonych stylów i opcji. (Przesłania [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Wywoływane przez platformę, aby narysować przycisk w okienku **polecenia** okna dialogowego **Dostosowywanie** . (Przesłania [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy zmieniono czcionkę globalną. (Przesłania [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton:: OnMove](#onmove)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi jest przenoszony. (Zastępuje [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)).|
|[CMFCToolBarEditBoxButton:: OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk zostanie widoczny lub niewidoczny. (Przesłania [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton:: OnSize](#onsize)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi zmienia jego rozmiar lub położenie, a ta zmiana powoduje zmianę rozmiaru przycisku. (Przesłania [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia. (Przesłania [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum. (Przesłania [CMFCToolBarButton:: serializować](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|`CMFCToolBarEditBoxButton::SetACCData`|Wypełnia udostępniony `CAccessibilityData` obiekt z danymi dostępności za pomocą przycisku paska narzędzi. (Przesłania [CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Ustawia tekst w kontrolce edycji przycisku.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)|Znajduje przycisk Edytuj kontrolkę o określonym IDENTYFIKATORze polecenia i ustawia tekst w kontrolce edycji tego przycisku.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Określa identyfikator zasobu menu skrótów, które jest skojarzone z przyciskiem.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Określa wygląd płaskich przycisków edycji w aplikacji.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Określa styl przycisku. (Zastępuje [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)).|

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola edycji do paska narzędzi, wykonaj następujące kroki:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

2. Konstruowanie `CMFCToolBarEditBoxButton` obiektu.

3. W programie obsługi komunikatów, który przetwarza komunikat AFX_WM_RESETTOOLBAR, Zastąp przycisk fikcyjny nowym przyciskiem pola kombi, używając [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji, [zobacz Przewodnik: Umieszczanie formantów na](../../mfc/walkthrough-putting-controls-on-toolbars.md)paskach narzędzi.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia różnych metod w `CMFCToolBarEditBoxButton` klasie. W przykładzie pokazano, jak określić, że użytkownik może rozciągnąć przycisk podczas dostosowywania, określić, że obramowanie przycisku ma być wyświetlane, gdy użytkownik kliknie przycisk, Ustaw tekst w kontrolce pole tekstowe, a następnie określ wygląd stylu płaskiego przycisków edycji w likacji kationy i Określanie stylu kontrolki pole edycji paska narzędzi.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbareditboxbutton. h

##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie platforma nie zezwala użytkownikowi na rozciąganie przycisku paska narzędzi podczas dostosowywania. Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) przez umożliwienie użytkownikowi rozciągnięcia przycisku paska narzędzi pola edycji podczas dostosowywania.

##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Konstruuje obiekt [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) .

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
podczas Określa identyfikator kontrolki.

*iImage*<br/>
podczas Określa indeks (liczony od zera) obrazu paska narzędzi. Obraz znajduje się w obiekcie [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) , który obsługuje Klasa klasy [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*dwStyle*<br/>
podczas Określa styl kontrolki edycji.

*iWidth*<br/>
podczas Określa szerokość (w pikselach) kontrolki edycji.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor ustawia styl kontrolki edycji do następującej kombinacji:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Domyślna szerokość kontrolki to 150 pikseli.

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Odwołanie do przycisku źródła, z którego ma zostać skopiowane.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skopiować kolejny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być typu `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>CMFCToolBarEditBoxButton:: SetEdit

Tworzy nową kontrolkę Edycja na przycisku.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Określa okno nadrzędne kontrolki edycji. Nie może mieć wartości NULL.

*cinania*<br/>
podczas Określa rozmiar i położenie kontrolki edycji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej kontrolki edycji; Jeśli Tworzenie i dołączanie kontrolki nie powiedzie się, ma ona wartość NULL.

### <a name="remarks"></a>Uwagi

`CMFCToolBarEditBoxButton` Obiekt jest konstruowany w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj metodę `CreateEdit`, która tworzy formant edycji systemu Windows i dołącza go `CMFCToolBarEditBoxButton` do obiektu.

##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Pobiera pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia do pobrania.

### <a name="return-value"></a>Wartość zwracana

Pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia lub ma wartość null, jeśli taki obiekt nie istnieje.

### <a name="remarks"></a>Uwagi

Ta metoda udostępniona narzędzia jest używana przez metody, takie jak [CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall) i [CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall) , aby ustawić lub pobrać tekst pierwszej kontrolki paska narzędzi pola edycji, która ma określony identyfikator polecenia.

##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Pobiera tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia, z którego ma zostać pobrana zawartość.

### <a name="return-value"></a>Wartość zwracana

`CString` Obiekt, który zawiera tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca pusty ciąg, jeśli żadne `CMFCToolBarEditBoxButton` obiekty nie mają określonego identyfikatora polecenia.

##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Pobiera identyfikator zasobu menu skrótów, które jest skojarzone z przyciskiem.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu skrótów, które jest skojarzone z przyciskiem lub 0, jeśli przycisk nie ma skojarzonego menu skrótów.

### <a name="remarks"></a>Uwagi

Struktura używa identyfikatora zasobu do tworzenia menu skrótów po kliknięciu przycisku prawym przyciskiem myszy.

##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Pobiera prostokąt związany z edycją części przycisku Edytuj pole.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parametry

*rectBorder*<br/>
określoną Odwołanie do `CRect` obiektu, który odbiera prostokąt powiązany.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera prostokąt ograniczenia kontrolki edycji we współrzędnych klienta. Rozszerza rozmiar prostokąta w każdym kierunku o jeden piksel.

Metoda [CMFCVisualManager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) wywołuje tę metodę, gdy rysuje obramowanie wokół `CMFCToolBarEditBoxButton` obiektu.

##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Zwraca wskaźnik do kontrolki [klasy CEdit](../../mfc/reference/cedit-class.md) , która jest osadzona w przycisku.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do kontrolki [klasy CEdit](../../mfc/reference/cedit-class.md) , która zawiera przycisk. Jeśli formant nie został jeszcze `CEdit` utworzony, ma wartość null.

### <a name="remarks"></a>Uwagi

`CEdit` Formant można utworzyć przez wywołanie [CMFCToolBarEditBoxButton:: SetEdit](#createedit).

##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton:: GetHwnd

Pobiera uchwyt okna skojarzony z przyciskiem paska narzędzi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna, który jest skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania metodę [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) poprzez zwrócenie uchwytu okna części kontrolki Edycja przycisku Edytuj.

##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Pobiera region obszaru klienckiego przycisku, który musi zostać narysowany ponownie.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Wartość zwracana

`CRect` Obiekt, który określa region, który musi być rysowany ponownie.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej, [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), przez uwzględnienie w regionie obszaru etykiety tekstowej.

##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Określa, czy obramowanie przycisku ma być wyświetlane po kliknięciu przycisku przez użytkownika.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przycisk wyświetla jego obramowanie po zaznaczeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej, [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), zwracając wartość różną od zera, jeśli formant jest widoczny.

##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton:: IsFlatMode

Określa, czy przyciski pola edycji mają styl płaski.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przyciski mają styl płaski; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie przyciski pola edycji mają styl płaski. Aby zmienić wygląd stylu prostego dla aplikacji, użyj metody [CMFCToolBarEditBoxButton::](#setflatmode) SetFlatMode.

##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Określa, czy przycisk przetwarza komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
podczas Komunikat z powiadomieniem, który jest skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk przetwarza komunikat WM_COMMAND lub wartość FALSE, aby wskazać, że komunikat musi być obsługiwany przez nadrzędny pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy zostanie wysłana wiadomość [WM_COMMAND](/windows/win32/menurc/wm-command) do okna nadrzędnego.

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie powiadomienia [EN_UPDATE](/windows/win32/Controls/en-update) . Dla każdego pola edycji z tym samym IDENTYFIKATORem polecenia co ten obiekt ustawia swoją etykietę tekstową na etykietę tekstową tego obiektu.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Wywoływane przez platformę, gdy przycisk zostanie dodany do okna dialogowego **Dostosowywanie** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) przez skopiowanie właściwości z kontrolki pole edycji na dowolnym pasku narzędzi, który ma ten sam identyfikator polecenia co ten obiekt. Ta metoda nie robi nic, jeśli żaden pasek narzędzi nie ma kontrolki pola edycji, która ma ten sam identyfikator polecenia co ten obiekt.

Aby uzyskać więcej informacji na temat **dostosowywania** okna dialogowego, zobacz [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Wywoływane przez platformę, gdy przycisk zostanie wstawiony do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) przez ponowne utworzenie obiektu wewnętrznego `CEdit` .

##  <a name="onclick"></a>CMFCToolBarEditBoxButton:: onkliknięcia

Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Przestrzeń.

*bDelay*<br/>
podczas Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: onkliknięciu](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)), zwracając wartość różną od zera, jeśli obiekt `CEdit` wewnętrzny jest widoczny.

##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*nCtlColor*<br/>
podczas Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do globalnego pędzla okna.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania implementację klasy bazowej ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) przez ustawienie kolorów tekstu i tła podanego kontekstu urządzenia odpowiednio do globalnego tekstu i kolorów tła.

Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Wywoływane przez platformę, gdy zmieniono czcionkę globalną.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionkę kontrolki na czcionkę globalną.

Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>CMFCToolBarEditBoxButton:: OnMove

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi jest przenoszony.

```
virtual void OnMove();
```

### <a name="remarks"></a>Uwagi

Ta metoda przesłania domyślną implementację klasy ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) przez zaktualizowanie pozycji obiektu wewnętrznego `CEdit`

##  <a name="onshow"></a>CMFCToolBarEditBoxButton:: OnShow

Wywoływane przez platformę, gdy przycisk zostanie widoczny lub niewidoczny.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
podczas Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość TRUE, przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)), wyświetlając przycisk, jeśli *bShow* ma wartość true. W przeciwnym razie ta metoda ukrywa przycisk.

##  <a name="onsize"></a>CMFCToolBarEditBoxButton:: OnSize

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi zmienia jego rozmiar lub położenie, a ta zmiana powoduje zmianę rozmiaru przycisku.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
podczas Nowa szerokość przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda przesłania domyślną implementację klasy, [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizując rozmiar i położenie obiektu wewnętrznego `CEdit` .

##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Przestrzeń.

*iButtonIndex*<br/>
podczas Przestrzeń.

*wndToolTip*<br/>
podczas Kontrolka wyświetlająca tekst etykietki narzędzia.

*str*<br/>
określoną `CString` Obiekt, który odbiera zaktualizowany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy bazowej ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) przez wyświetlanie tekstu etykietki narzędzia, która jest skojarzona z częścią edycji przycisku. Jeśli obiekt wewnętrzny `CEdit` ma wartość null lub uchwyt `CEdit` okna obiektu nie identyfikuje istniejącego okna, ta metoda nie wykonuje żadnych operacji i zwraca wartość false.

##  <a name="setcontents"></a>CMFCToolBarEditBoxButton:: setcontents

Ustawia tekst w kontrolce pole tekstowe.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parametry

*sContents*<br/>
podczas Określa nowy tekst do ustawienia.

##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Znajduje obiekt [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) o określonym identyfikatorze polecenia i ustawia określony tekst w polu tekstowym.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Określa identyfikator polecenia kontrolki, dla którego zostanie zmieniony tekst.

*strContents*<br/>
podczas Określa nowy tekst do ustawienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli tekst został ustawiony; 0, `CMFCToolBarEditBoxButton` Jeśli kontrolka o określonym identyfikatorze polecenia nie istnieje.

##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Określa identyfikator zasobu menu skrótów, które jest skojarzone z przyciskiem.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator zasobu menu skrótów.

### <a name="remarks"></a>Uwagi

Struktura używa identyfikatora zasobu do tworzenia menu skrótów po kliknięciu prawym przyciskiem myszy przycisku paska narzędzi.

##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton:: SetFlatMode

Określa wygląd płaskich przycisków edycji w aplikacji.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
podczas Styl płaski przycisków edycji. Jeśli ten parametr ma wartość TRUE, wygląd stylu płaskiego jest włączony; w przeciwnym razie wygląd stylu płaskiego jest wyłączony.

### <a name="remarks"></a>Uwagi

Domyślny styl płaski przycisków edycji ma wartość TRUE. Użyj metody [CMFCToolBarEditBoxButton::](#isflatmode) IsFlatMode, aby pobrać prosty wygląd stylu aplikacji.

##  <a name="setstyle"></a>CMFCToolBarEditBoxButton:: SetStyle

Określa styl kontrolki pola edycji paska narzędzi.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
podczas Nowy styl do ustawienia.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) na *nStyle* również wyłącza pole tekstowe, gdy aplikacja jest w trybie dostosowywania, i włącza ją, gdy aplikacja nie jest w trybie dostosowywania (zobacz [CMFCToolBar::](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) setdostosowywaniemode i [CMFCToolBar::](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)isdostosowywaniemode). Zobacz [Style formantów paska narzędzi](../../mfc/reference/toolbar-control-styles.md) , aby wyświetlić listę prawidłowych flag stylów.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
