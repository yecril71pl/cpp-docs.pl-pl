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
ms.openlocfilehash: 064ebe1c8fe377064d410d09e5ef60ed628df2f3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754001"
---
# <a name="cmfctoolbareditboxbutton-class"></a>Klasa CMFCToolBarEditBoxButton

Przycisk paska narzędzi zawierający kontrolkę edycji ( [CEdit Class](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Składnia

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Konstruuje `CMFCToolBarEditBoxButton` obiekt.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania. (Zastępuje [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku. (Zastępuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::UtwórzEdytuj](#createedit)|Tworzy nowy kontrolkę edycji w przycisku.|
|`CMFCToolBarEditBoxButton::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Pobiera tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Pobiera identyfikator zasobu menu skrótów skojarzonego z przyciskiem.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Pobiera prostokąt ograniczający części edycji przycisku pola edycji.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Zwraca wskaźnik do formantu edycji osadzonego w przycisku.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Pobiera uchwyt okna, który jest skojarzony z przyciskiem paska narzędzi. (Zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Pobiera region obszaru klienta przycisku, który musi zostać ponownie narysowany. (Zastępuje [przycisk CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku jest wyświetlane, gdy użytkownik kliknie przycisk. (Zastępuje [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski pola edycji mają styl płaski.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza komunikat [WM_COMMAND.](/windows/win32/menurc/wm-command) (Zastępuje [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez strukturę, gdy przycisk jest dodawany do **dostosowywania** okna dialogowego. (Zastępuje [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Wywoływana przez strukturę, aby obliczyć rozmiar przycisku dla określonego kontekstu urządzenia i stanu dokowania. (Zastępuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Zastępuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Wywoływana przez strukturę, gdy użytkownik kliknie przycisk myszy. (Zastępuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR. (Zastępuje [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Wywoływane przez strukturę, aby narysować przycisk przy użyciu określonych stylów i opcji. (Zastępuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Wywoływane przez strukturę, aby narysować przycisk w okienku **Polecenia** okna dialogowego **Dostosowywanie.** (Zastępuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsZmienił](#onglobalfontschanged)|Wywoływana przez platformę po zmianie czcionki globalnej. (Zastępuje [CMFCToolBarButton::OnGlobalFontsZmieniem).)](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Wywoływane przez strukturę, gdy przesuwa się nadrzędny pasek narzędzi. (Zastępuje [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Wywoływane przez strukturę, gdy przycisk staje się widoczne lub niewidoczne. (Zastępuje [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::Rozmiar](#onsize)|Wywoływana przez platformę, gdy nadrzędny pasek narzędzi zmienia swój rozmiar lub położenie, a ta zmiana powoduje, że przycisk zmienia rozmiar. (Zastępuje [cmfctoolbarbutton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia. (Zastępuje [przycisk CMFCToolBarButton::OnUpdateToolTip.)](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)|
|`CMFCToolBarEditBoxButton::Serialize`|Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum. (Zastępuje [przycisk CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Wypełnia dostarczony `CAccessibilityData` obiekt danymi ułatwień dostępu z przycisku paska narzędzi. (Zastępuje [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Ustawia tekst w formancie edycji przycisku.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Znajduje przycisk sterowania edycją o określonym identyfikatorze polecenia i ustawia tekst w formancie edycji tego przycisku.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Określa identyfikator zasobu menu skrótów skojarzonego z przyciskiem.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Określa wygląd stylu płaskiego przycisków pola edycji w aplikacji.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Określa styl przycisku. (Zastępuje [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola edycji do paska narzędzi, wykonaj następujące czynności:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

2. Konstruuj `CMFCToolBarEditBoxButton` obiekt.

3. W programie obsługi wiadomości, który przetwarza komunikat AFX_WM_RESETTOOLBAR, zastąp przycisk manekina nowym przyciskiem pola kombi za pomocą [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji, zobacz [Przewodnik: Umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarEditBoxButton` używać różnych metod w klasie. W przykładzie pokazano, jak określić, że użytkownik może rozciągnąć przycisk podczas dostosowywania, określić, że obramowanie przycisku jest wyświetlane, gdy użytkownik kliknie przycisk, ustawić tekst w formancie pola tekstowego, określić wygląd stylu płaskiego przycisków pola edycji w aplikacji i określić styl kontrolki pola edycji paska narzędzi.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbareditboxbutton.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Określa, czy użytkownik może rozciągnąć przycisk podczas dostosowywania.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie zezwala użytkownikowi na rozciąganie przycisku paska narzędzi podczas dostosowywania. Ta metoda rozszerza implementacji klasy podstawowej [(CMFCToolBarButton::CanBeStretched),](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)umożliwiając użytkownikowi rozciągnąć przycisk paska narzędzi edycji podczas dostosowywania.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Konstruuje [obiekt CMFCToolBarEditBoxButton.](../../mfc/reference/cmfctoolbareditboxbutton-class.md)

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Określa identyfikator formantu.

*Iimage*<br/>
[w] Określa indeks od zera obrazu paska narzędzi. Obraz znajduje się w [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md) obiektu, który [cmfctoolbar klasy](../../mfc/reference/cmfctoolbar-class.md) utrzymuje.

*Dwstyle*<br/>
[w] Określa styl sterowania edycją.

*iWidth ( iWidth )*<br/>
[w] Określa szerokość w pikselach formantu edycji.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor ustawia styl sterowania edycją na następującą kombinację:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

Domyślna szerokość formantu wynosi 150 pikseli.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom

Kopiuje właściwości innego przycisku paska narzędzi do bieżącego przycisku.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Odwołanie do przycisku źródłowego, z którego mają być kopiowane.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *src* musi być `CMFCToolBarEditBoxButton`typu .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarEditBoxButton::UtwórzEdytuj

Tworzy nowy kontrolkę edycji w przycisku.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Określa okno nadrzędne formantu edycji. Nie może być null.

*Rect*<br/>
[w] Określa rozmiar i położenie formantu edycji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego formantu edycji; jest null, jeśli tworzenie i przywiązanie formantu nie powiedzie się.

### <a name="remarks"></a>Uwagi

Konstruowanie `CMFCToolBarEditBoxButton` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `CreateEdit`, co `CMFCToolBarEditBoxButton` tworzy formant edycji systemu Windows i dołącza go do obiektu.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Pobiera pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku do pobrania.

### <a name="return-value"></a>Wartość zwracana

Pierwszy `CMFCToolBarEditBoxButton` obiekt w aplikacji, który ma określony identyfikator polecenia lub NULL, jeśli taki obiekt nie istnieje.

### <a name="remarks"></a>Uwagi

Ta udostępniona metoda narzędzia jest używana przez metody takie jak [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) i [CMFCToolBarEditBoxButton::GetContentsAll,](#getcontentsall) aby ustawić lub uzyskać tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Pobiera tekst pierwszego formantu paska narzędzi pola edycji, który ma określony identyfikator polecenia.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku, z którego ma być pobierana zawartość.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający tekst pierwszego formantu paska narzędzi edycji o określonym identyfikatorze polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca pusty `CMFCToolBarEditBoxButton` ciąg, jeśli żadne obiekty nie mają określonego identyfikatora polecenia.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Pobiera identyfikator zasobu menu skrótów skojarzonego z przyciskiem.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu skrótów skojarzonego z przyciskiem lub 0, jeśli przycisk nie ma skojarzonego menu skrótów.

### <a name="remarks"></a>Uwagi

Struktura używa identyfikatora zasobu do tworzenia menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy przycisk.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Pobiera prostokąt ograniczający części edycji przycisku pola edycji.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parametry

*rectBorder*<br/>
[na zewnątrz] Odwołanie do `CRect` obiektu, który odbiera prostokąt ograniczający.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera prostokąt ograniczający formantu edycji we współrzędnych klienta. Rozszerza rozmiar prostokąta w każdym kierunku o jeden piksel.

[METODA CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) wywołuje tę metodę, gdy `CMFCToolBarEditBoxButton` rysuje obramowanie wokół obiektu.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Zwraca wskaźnik do [cEdit klasy](../../mfc/reference/cedit-class.md) kontroli, który jest osadzony w przycisku.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [cEdit klasy](../../mfc/reference/cedit-class.md) kontroli, który zawiera przycisk. Jest null, `CEdit` jeśli formant nie został jeszcze utworzony.

### <a name="remarks"></a>Uwagi

`CEdit` Formant można utworzyć, wywołując [polecenie CMFCToolBarEditBoxButton::CreateEdit](#createedit).

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

Pobiera uchwyt okna, który jest skojarzony z przyciskiem paska narzędzi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna, który jest skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody zwracanie dojścia okna części kontroli edycji przycisku pola edycji.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Pobiera region obszaru klienta przycisku, który musi zostać ponownie narysowany.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CRect` który określa region, który musi zostać ponownie narysowany.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), przez włączenie w regionie obszaru etykiety tekstowej.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Określa, czy obramowanie przycisku jest wyświetlane, gdy użytkownik kliknie przycisk.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk wyświetla obramowanie po wybraniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), zwracając wartość niezerową, jeśli formant jest widoczny.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

Określa, czy przyciski pola edycji mają styl płaski.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przyciski mają płaski styl; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie przyciski pola edycji mają styl płaski. Użyj [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) metody, aby zmienić wygląd stylu płaskiego dla aplikacji.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Określa, czy przycisk przetwarza komunikat [WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*Kod iNotifyCode*<br/>
[w] Komunikat powiadomienia skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk przetwarza komunikat WM_COMMAND lub FALSE, aby wskazać, że wiadomość musi być obsługiwana przez nadrzędny pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy ma zamiar wysłać wiadomość [WM_COMMAND](/windows/win32/menurc/wm-command) do okna nadrzędnego.

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [powiadomienia EN_UPDATE.](/windows/win32/Controls/en-update) Dla każdego pola edycji o tym samym identyfikatorze polecenia co ten obiekt ustawia etykietę tekstową na etykietę tekstową tego obiektu.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Wywoływane przez strukturę, gdy przycisk jest dodawany do **dostosowywania** okna dialogowego.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) przez skopiowanie właściwości z kontrolki pola edycji w dowolnym pasku narzędzi, który ma ten sam identyfikator polecenia jako ten obiekt. Ta metoda nic nie robi, jeśli żaden pasek narzędzi nie ma formantu pola edycji, który ma ten sam identyfikator polecenia co ten obiekt.

Aby uzyskać więcej informacji na temat okna dialogowego **Dostosowywanie,** zobacz [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Wywoływana przez strukturę, gdy przycisk jest wstawiany do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do nowego okna nadrzędnego.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd) `CEdit` ) przez odtworzenie obiektu wewnętrznego.

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick

Wywoływana przez strukturę, gdy użytkownik kliknie przycisk myszy.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Nieużywane.

*bDelay (własówce)*<br/>
[w] Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przycisk przetwarza komunikat kliknięcia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) przez zwrócenie `CEdit` wartości niezerowej, jeśli obiekt wewnętrzny jest widoczny.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi obsługuje komunikat WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*nCtlColor ( nCtlColor )*<br/>
[w] Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Dojście do globalnego pędzla okien.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) przez ustawienie tekstu i kolorów tła kontekstu urządzenia pod warunkiem, do tekstu globalnego i kolorów tła, odpowiednio.

Aby uzyskać więcej informacji na temat opcji globalnych dostępnych dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsZmienił

Wywoływana przez platformę po zmianie czcionki globalnej.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) zmieniając czcionkę formantu do czcionki globalnej.

Aby uzyskać więcej informacji na temat opcji globalnych dostępnych dla aplikacji, zobacz [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

Wywoływane przez strukturę, gdy przesuwa się nadrzędny pasek narzędzi.

```
virtual void OnMove();
```

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) `CEdit` przez aktualizowanie pozycji obiektu wewnętrznego

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

Wywoływane przez strukturę, gdy przycisk staje się widoczne lub niewidoczne.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość PRAWDA, przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) przez wyświetlenie przycisku, jeśli *bShow* jest TRUE. W przeciwnym razie ta metoda ukrywa przycisk.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarEditBoxButton::Rozmiar

Wywoływana przez platformę, gdy nadrzędny pasek narzędzi zmienia swój rozmiar lub położenie, a ta zmiana powoduje, że przycisk zmienia rozmiar.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*rozmiar iSize*<br/>
[w] Nowa szerokość przycisku w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje domyślną implementację klasy [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizując `CEdit` rozmiar i położenie obiektu wewnętrznego.

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

Wywoływane przez platformę, gdy nadrzędny pasek narzędzi aktualizuje tekst etykietki narzędzia.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Nieużywane.

*iButtonIndex*<br/>
[w] Nieużywane.

*wndToolTip*<br/>
[w] Formant, który wyświetla tekst etykietki narzędzia.

*Str*<br/>
[na zewnątrz] Obiekt, `CString` który odbiera zaktualizowany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) przez wyświetlanie tekstu etykietki narzędzia, który jest skojarzony z częścią edycji przycisku. Jeśli obiekt `CEdit` wewnętrzny ma wartość NULL `CEdit` lub uchwyt okna obiektu nie identyfikuje istniejącego okna, ta metoda nic nie robi i zwraca wartość FAŁSZ.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Ustawia tekst w formancie pola tekstowego.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parametry

*sContents*<br/>
[w] Określa nowy tekst do ustawionego.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Znajduje [obiekt CMFCToolBarEditBoxButton,](../../mfc/reference/cmfctoolbareditboxbutton-class.md) który ma określony identyfikator polecenia i ustawia określony tekst w jego polu tekstowym.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Określa identyfikator polecenia formantu, dla którego tekst zostanie zmieniony.

*strContents*<br/>
[w] Określa nowy tekst do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli tekst został ustawiony; 0, `CMFCToolBarEditBoxButton` jeśli formant o określonym identyfikatorze polecenia nie istnieje.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Określa identyfikator zasobu menu skrótów skojarzonego z przyciskiem.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator zasobu w menu skrótów.

### <a name="remarks"></a>Uwagi

Struktura używa identyfikatora zasobu do utworzenia menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy przycisk paska narzędzi.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Określa wygląd stylu płaskiego przycisków pola edycji w aplikacji.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat (ur.*<br/>
[w] Płaski styl przycisków pola edycji. Jeśli ten parametr ma wartość PRAWDA, włączony jest wygląd stylu płaskiego; w przeciwnym razie wygląd stylu płaskiego jest wyłączony.

### <a name="remarks"></a>Uwagi

Domyślnym stylem płaskim dla przycisków pola edycji jest PRAWDA. Użyj [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) metody, aby pobrać wygląd stylu płaskiego dla aplikacji.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle

Określa styl kontrolki pola edycji paska narzędzi.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*styl nStyle*<br/>
[w] Nowy styl do skonfigurowania.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) do *nStyle* Wyłącza również pole tekstowe, gdy aplikacja jest w trybie Dostosuj i włącza go, gdy aplikacja nie jest w trybie Dostosuj (zobacz [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) i [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Zobacz [Style sterowania paskiem narzędzi,](../../mfc/reference/toolbar-control-styles.md) aby uzyskać listę prawidłowych flag stylu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
