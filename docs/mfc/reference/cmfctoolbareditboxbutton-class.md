---
title: Klasa CMFCToolBarEditBoxButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffb78d1c7893255666e5a340ce48649da72df6c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706904"
---
# <a name="cmfctoolbareditboxbutton-class"></a>Klasa CMFCToolBarEditBoxButton
Przycisk paska narzędzi, który zawiera kontrolkę edycji ( [klasa CEdit](../../mfc/reference/cedit-class.md)).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Konstruuje `CMFCToolBarEditBoxButton` obiektu.|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Określa, czy użytkownik rozciągnąć przycisku podczas dostosowywania. (Przesłania [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Tworzy nową kontrolkę edycji przycisku.|  
|`CMFCToolBarEditBoxButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarEditBoxButton` obiektu w aplikacji, która ma identyfikator określonego polecenia.|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Pobiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Pobiera identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Pobiera prostokąt otaczający edycji część przycisk pola edycji.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Zwraca wskaźnik do kontrolki edycji, który jest osadzony w przycisku.|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Pobiera uchwyt okna, który jest skojarzony z przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Pobiera region obszaru klienckiego przycisku, który musi być narysowany ponownie. (Przesłania [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku jest wyświetlany, gdy użytkownik kliknie przycisk. (Przesłania [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski okno edycji mają płaskie stylu.|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości. (Przesłania [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Metoda wywoływana przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, obsługując narzędzi nadrzędnego wm_ctlcolor — komunikat. (Przesłania [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarEditBoxButton::OnDraw`|Metoda wywoływana przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy zmieniono globalnego czcionki. (Przesłania [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Wywoływane przez platformę, gdy przemieszczane narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk staje się widoczny lub niewidoczny. (Przesłania [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar. (Przesłania [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy narzędzi nadrzędnego aktualizuje jego tekst etykietki narzędzia. (Przesłania [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarEditBoxButton::Serialize`|Odczytuje obiekt z archiwum lub zapisuje je do archiwum. (Przesłania [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarEditBoxButton::SetACCData`|Wypełnia podane `CAccessibilityData` obiektu o dostępność danych na przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Ustawia tekst w kontrolce edycji przycisku.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Umożliwia znalezienie przycisk kontrolki edycji, który ma identyfikator określonego polecenia i ustawia tekst w kontrolce edycji tego przycisku.|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Określa identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Określa płaski wygląd przycisków okno edycji w aplikacji.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Określa styl przycisku. (Przesłania [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać przycisk pola edycji do paska narzędzi, wykonaj następujące kroki:  
  
 1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi.  
  
 2. Konstruowania `CMFCToolBarEditBoxButton` obiektu.  
  
 3. Programu obsługi wiadomości, która przetwarza komunikat AFX_WM_RESETTOOLBAR, Zamień zastępczy przycisk Nowy przycisk pola kombi przy użyciu [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCToolBarEditBoxButton` klasy. W przykładzie pokazano, jak określić, czy użytkownika można rozciągnąć przycisku podczas dostosowywania, określ, czy obramowanie przycisku są wyświetlane, gdy użytkownik kliknie przycisk, ustawiać tekst w polu tekstowym, określ płaski wygląd przycisków okno edycji w nazwę aplikacji i określ styl paska narzędzi edycji formantu pola.  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched  
 Określa, czy użytkownik rozciągnąć przycisku podczas dostosowywania.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wartość TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie struktura nie zezwala użytkownikowi stretch przycisku paska narzędzi podczas dostosowywania. Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), umożliwiając użytkownikowi stretch przycisku paska narzędzi okno edycji podczas dostosowywania.  
  
##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 Konstruuje [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) obiektu.  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
*uiID*<br/>
[in] Określa identyfikator kontrolki.  
  
*iImage*<br/>
[in] Określa liczony od zera indeks obrazu paska narzędzi. Obraz, który znajduje się w [klasa CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiekt [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) przechowuje klasy.  
  
*dwStyle*<br/>
[in] Określa styl kontrolki edycji.  
  
*iWidth*<br/>
[in] Określa szerokość w pikselach kontrolki edycji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny konstruktor ustawia styl formantu edycji następujących kombinacji:  
  
 WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL  
  
 Domyślna szerokość kontrolki to 150 pikseli.  
  
##  <a name="copyfrom"></a>  CMFCToolBarEditBoxButton::CopyFrom  
 Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *SRC* musi być typu `CMFCToolBarEditBoxButton`.  
  
##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit  
 Tworzy nową kontrolkę edycji przycisku.  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Określa okno nadrzędne kontrolki edycji. Nie może być równa NULL.  
  
*Rect*<br/>
[in] Określa rozmiar i położenie kontrolki edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do kontrolki edycji nowo utworzony; ma wartość NULL, jeśli tworzenie i dołączanie formantu nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CMFCToolBarEditBoxButton` obiektu w dwóch krokach. Pierwsze wywołanie konstruktora, a następnie wywołaj `CreateEdit`, który tworzy Windows formantu edycyjnego i dołącza go do `CMFCToolBarEditBoxButton` obiektu.  
  
##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd  
 Pobiera pierwszy `CMFCToolBarEditBoxButton` obiektu w aplikacji, która ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisku do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy `CMFCToolBarEditBoxButton` obiektu w aplikacji, który zawiera polecenie o określonym identyfikatorze lub o wartości NULL, jeśli taki obiekt nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda narzędzia udostępnione jest używana przez metody takie jak [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) i [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) można ustawiać ani pobierać tekst pierwszego narzędzi pole edycji formant, który ma identyfikator określonego polecenia.  
  
##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll  
 Pobiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisku, z którego można pobrać zawartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który zawiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pusty ciąg, jeśli nie `CMFCToolBarEditBoxButton` obiektów ma identyfikator określonego polecenia.  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID  
 Pobiera identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu skrótów, które są skojarzone z przycisku lub 0, jeśli przycisk ma menu skrótów skojarzone nie.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko wykorzystuje identyfikator zasobu, aby utworzyć menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy na przycisku.  
  
##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder  
 Pobiera prostokąt otaczający edycji część przycisk pola edycji.  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>Parametry  
*rectBorder*<br/>
[out] Odwołanie do `CRect` obiekt, który odbiera prostokąt otaczający.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera prostokąt otaczający kontrolki edycji we współrzędnych klienta. Rozmiar prostokąta w każdym kierunku jego rozwija o jeden piksel.  
  
 [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) metoda wywołuje tę metodę, gdy jej rysuje obramowanie wokół `CMFCToolBarEditBoxButton` obiektu.  
  
##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox  
 Zwraca wskaźnik do [klasa CEdit](../../mfc/reference/cedit-class.md) formant, który jest osadzony w przycisku.  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [klasa CEdit](../../mfc/reference/cedit-class.md) kontrolki, która zawiera przycisk. Ma wartość NULL, jeśli `CEdit` formant nie został jeszcze utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CEdit` kontroli przez wywołanie metody [CMFCToolBarEditBoxButton::CreateEdit](#createedit).  
  
##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd  
 Pobiera uchwyt okna, który jest skojarzony z przycisku paska narzędzi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna, który jest skojarzony z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody, zwracając uchwyt okna Edytuj części kontrolki przycisk pola edycji.  
  
##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect  
 Pobiera region obszaru klienckiego przycisku, który musi być narysowany ponownie.  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` obiekt, który określa region, który musi być narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), umieszczając w regionie obszaru tekst etykiety.  
  
##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder  
 Określa, czy obramowanie przycisku jest wyświetlany, gdy użytkownik kliknie przycisk.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk powoduje wyświetlenie jego obramowanie po wybraniu; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), zwracając wartość różną od zera, jeśli kontrolka jest widoczna.  
  
##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode  
 Określa, czy przyciski okno edycji mają płaskie stylu.  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przyciski płaski; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie przyciski okno edycji mają płaskie stylu. Użyj [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) metodą zmiany warstwy płaski wygląd aplikacji.  
  
##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand  
 Określa, czy przycisk przetwarza [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
*iNotifyCode*<br/>
[in] Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk przetwarza komunikatów WM_COMMAND lub wartość FALSE wskazuje, że wiadomości muszą być obsługiwane przez narzędzi nadrzędnej.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę po około do wysyłania [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości do okna nadrzędnego.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [EN_UPDATE](/windows/desktop/Controls/en-update) powiadomień. Dla każdego pola edycji z tym samym Identyfikatorem polecenia, jak ten obiekt ustawia jego etykieta tekstowa etykietę tekstową tego obiektu.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) przez skopiowanie właściwości formant pola edycji w dowolnym pasek narzędzi, który ma ten sam identyfikator polecenia, jak ten obiekt. Ta metoda nie działają, jeśli brak paska narzędzi zawiera formant pola edycji, który ma ten sam identyfikator polecenia, jak ten obiekt.  
  
 Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik do nowego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), ponownie tworząc wewnętrzny `CEdit` obiektu.  
  
##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*pWnd*<br/>
[in] Nieużywane.  
  
*bDelay*<br/>
[in] Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)), zwracając wartość różną od zera, jeśli wewnętrzny `CEdit` obiekt jest widoczny.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor  
 Wywoływane przez platformę, obsługując narzędzi nadrzędnego wm_ctlcolor — komunikat.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
*nCtlColor*<br/>
[in] Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do pędzla okno globalnych.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)), ustawiając kolory tekstu i tła kontekstu urządzenia podanego tekstu globalnego i kolory tła, odpowiednio.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 Wywoływane przez platformę, gdy zmieniono globalnego czcionki.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionki formantu z globalnego czcionki.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove  
 Wywoływane przez platformę, gdy przemieszczane narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślna Implementacja klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), aktualizując pozycji wewnętrznego `CEdit` obiektu  
  
##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow  
 Wywoływane przez platformę, gdy przycisk staje się widoczny lub niewidoczny.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
*bShow*<br/>
[in] Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość TRUE, ten przycisk jest widoczna. W przeciwnym razie przycisk nie jest widoczna.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) za pomocą wyświetlania przycisku, jeśli *bShow* ma wartość TRUE. W przeciwnym razie ta metoda powoduje ukrycie przycisku.  
  
##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
*iSize*<br/>
[in] Szerokość nowy przycisk, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślna Implementacja klasy [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizując rozmiar i położenie wewnętrznego `CEdit` obiektu.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego aktualizuje jego tekst etykietki narzędzia.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Nieużywane.  
  
*iButtonIndex*<br/>
[in] Nieużywane.  
  
*wndToolTip*<br/>
[in] Formant, który wyświetla tekst etykietki narzędzia.  
  
*str*<br/>
[out] A `CString` obiekt, który odbiera tekst etykietki narzędzia zaktualizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)), wyświetlając tekst etykietki narzędzia, skojarzony z części edycji przycisku. Jeśli wewnętrzny `CEdit` obiektu ma wartość NULL lub uchwyt okna `CEdit` obiektu nie identyfikuje istniejącego okna, ta metoda nic nie robi i zwraca wartość FALSE.  
  
##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents  
 Ustawia tekst w polu tekstowym.  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>Parametry  
*sContents*<br/>
[in] Określa nowy tekst do ustawienia.  
  
##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll  
 Umożliwia znalezienie [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) obiekt, który ma identyfikator określonego polecenia i ustawia określony tekst w jego polu tekstowym.  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Określa identyfikator polecenia kontroli, dla którego zostanie zmieniony tekst.  
  
*strContents*<br/>
[in] Określa nowy tekst do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli ustawiono tekst; 0, jeśli `CMFCToolBarEditBoxButton` formant z polecenie o określonym identyfikatorze nie istnieje.  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID  
 Określa identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator zasobu menu skrótów.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko wykorzystuje identyfikator zasobu, aby utworzyć menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy przycisk na pasku narzędzi.  
  
##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode  
 Określa płaski wygląd przycisków okno edycji w aplikacji.  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bFlat*<br/>
[in] Płaski przycisków pola edycji. Jeśli ten parametr ma wartość TRUE, płaski wygląd jest włączony; w przeciwnym razie płaski wygląd jest wyłączona.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny styl płaskie przyciski okno edycji ma wartość TRUE. Użyj [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) metodę, która pobierze płaski wygląd aplikacji.  
  
##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle  
 Określa styl pasek narzędzi edycji formantu pola.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
*nStyle*<br/>
[in] Nowy styl do ustawienia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) do *nStyle* go wyłącza również pola tekstowego, gdy aplikacja jest w trybie Dostosuj i włączy ją, gdy aplikacja nie jest w trybie Dostosuj (patrz [ CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) i [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md) listę flag prawidłowe stylu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



