---
title: Klasa CMFCToolBarEditBoxButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f774282823d68a3b5f2107b7297714ce8aa918f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbareditboxbutton-class"></a>Klasa CMFCToolBarEditBoxButton
Przycisk paska narzędzi zawierający formant edycyjny ( [CEdit klasy](../../mfc/reference/cedit-class.md)).  
  
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
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Określa, czy użytkownik może stretch przycisku w trakcie dostosowywania realizowanego. (Przesłania [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Tworzy nowy formant edycji w przycisku.|  
|`CMFCToolBarEditBoxButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarEditBoxButton` obiektu w aplikacji, która ma identyfikator określonego polecenia.|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Pobiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Pobiera identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Pobiera prostokąt ograniczający edycji części przycisk pola edycji.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Zwraca wskaźnik do kontrolki edycji, który jest osadzony w przycisku.|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Pobiera uchwytu okna, który jest skojarzony z przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Pobiera region obszaru klienckiego przycisku, który musi zostać narysowany ponownie. (Przesłania [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Określa, czy obramowania przycisku jest wyświetlany, gdy użytkownik kliknie przycisk. (Przesłania [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski pole edycji mają płaski.|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości. (Przesłania [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Wywoływane przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, obsługując narzędzi nadrzędnej `WM_CTLCOLOR` wiadomości. (Przesłania [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarEditBoxButton::OnDraw`|Wywoływane przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy globalne czcionka została zmieniona. (Przesłania [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Wywoływane przez platformę, gdy przesuwa narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk jest widoczny, czy niewidoczne. (Przesłania [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar. (Przesłania [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy jego tekst etykietki narzędzia aktualizacji narzędzi nadrzędnego. (Przesłania [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarEditBoxButton::Serialize`|Odczytuje obiekt z archiwum i zapisuje go do archiwum. (Przesłania [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarEditBoxButton::SetACCData`|Wypełnia dostarczonych `CAccessibilityData` obiektu ułatwień dostępu danymi z przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Ustawia tekst w formancie edycyjnym przycisku.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Znajduje się przycisk formantu edycji, który ma polecenie o określonym identyfikatorze i ustawia tekst w formancie edycyjnym przycisku.|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Określa identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Określa wygląd płaski przycisków pola edycji w aplikacji.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Określa styl przycisku. (Przesłania [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać dostępny przycisk Edytuj pola na pasku narzędzi, wykonaj następujące kroki:  
  
 1. Zarezerwować Identyfikatora fikcyjnego zasobu dla przycisku w zasobie nadrzędnym paska narzędzi.  
  
 2. Utworzyć `CMFCToolBarEditBoxButton` obiektu.  
  
 3. Programu obsługi wiadomości, który przetwarza `AFX_WM_RESETTOOLBAR` komunikatów, Zastąp fikcyjny przycisk Nowy przycisk pole kombi za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCToolBarEditBoxButton` klasy. W przykładzie przedstawiono sposób określić, czy użytkownika można stretch przycisku w trakcie dostosowywania realizowanego, określ, czy obramowania przycisku jest wyświetlane, gdy użytkownik kliknie przycisk, ustawić tekst w polu tekstowym, określ płaski wygląd przycisków pola edycji w nazwę kalizacja i określ styl paska narzędzi edycji kontrolki pola.  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched  
 Określa, czy użytkownik może stretch przycisku w trakcie dostosowywania realizowanego.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie platformę nie Zezwalaj użytkownikowi na stretch przycisku paska narzędzi w trakcie dostosowywania realizowanego. Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), umożliwiając użytkownikowi stretch przycisku paska narzędzi pole edycji w trakcie dostosowywania realizowanego.  
  
##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 Konstruuje [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) obiektu.  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiID`  
 Określa identyfikator formantu.  
  
 [in]`iImage`  
 Określa liczony od zera indeks obrazu paska narzędzi. Obraz znajduje się w [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiekt, który [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) obsługuje klasy.  
  
 [in]`dwStyle`  
 Określa styl formantu edycji.  
  
 [in]`iWidth`  
 Określa szerokość w pikselach kontrolki edycji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny konstruktor ustawia styl formantu edycji następujących kombinacji:  
  
 `WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL`  
  
 Domyślna szerokość formantu jest 150 pikseli.  
  
##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom  
 Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
 Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. `src`musi być typu `CMFCToolBarEditBoxButton`.  
  
##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit  
 Tworzy nowy formant edycji w przycisku.  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pWndParent`  
 Określa okno nadrzędne kontrolki edycji. Nie może być wartością NULL.  
  
 `[in] rect`  
 Określa rozmiar i położenie kontrolki edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonej edycji; jest `NULL` Jeśli tworzenie formantu i załącznika nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CMFCToolBarEditBoxButton` obiektu w dwóch krokach. Pierwsze wywołanie konstruktora, a następnie wywołać `CreateEdit`, która tworzy kontrolkę edycji systemu Windows i dołącza go do `CMFCToolBarEditBoxButton` obiektu.  
  
##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd  
 Pobiera pierwszy `CMFCToolBarEditBoxButton` obiektu w aplikacji, która ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisku do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy `CMFCToolBarEditBoxButton` obiektów w aplikacji, która ma identyfikator określonego polecenia lub `NULL` Jeśli nie istnieje żaden taki obiekt.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jako narzędzia udostępnione jest używana przez metody, takie jak [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) i [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) ustawić lub pobrać tekst pierwszego narzędzi pole edycji formant, który ma identyfikator określonego polecenia.  
  
##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll  
 Pobiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisku, z którego można pobrać zawartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który zawiera tekst pierwszego edycji okno narzędzi formantu, który ma identyfikator określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pusty ciąg, jeśli nie `CMFCToolBarEditBoxButton` obiektów ma identyfikator określonego polecenia.  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID  
 Pobiera identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu skrótów, który jest skojarzony z przycisku lub 0, jeśli menu skrótów skojarzone nie ma przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa Identyfikatora zasobu do utworzenia menu skrótów po kliknięciu przycisku.  
  
##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder  
 Pobiera prostokąt ograniczający edycji części przycisk pola edycji.  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectBorder`  
 Odwołanie do `CRect` obiekt, który odbiera prostokątem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera prostokąt ograniczający edycji formantu we współrzędnych klienta. Rozszerza on rozmiar prostokąta w każdym kierunku przez jeden piksel.  
  
 [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) metoda wywołuje tę metodę, gdy go rysuje obramowanie wokół `CMFCToolBarEditBoxButton` obiektu.  
  
##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox  
 Zwraca wskaźnik do [klasy CEdit](../../mfc/reference/cedit-class.md) formant, który jest osadzony w przycisku.  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [klasy CEdit](../../mfc/reference/cedit-class.md) formant, który zawiera przycisk. Jest `NULL` Jeśli `CEdit` formantu nie została jeszcze utworzona.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CEdit` kontroli przez wywołanie metody [CMFCToolBarEditBoxButton::CreateEdit](#createedit).  
  
##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd  
 Pobiera uchwytu okna, który jest skojarzony z przycisku paska narzędzi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna, który jest skojarzony z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metoda zwróciła uchwytu okna kontrolki edycji części przycisk pola edycji.  
  
##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect  
 Pobiera region obszaru klienckiego przycisku, który musi zostać narysowany ponownie.  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` obiekt, który określa region, który musi zostać narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), umieszczając w regionie obszarze tekst etykiety.  
  
##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder  
 Określa, czy obramowania przycisku jest wyświetlany, gdy użytkownik kliknie przycisk.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku wyświetla jego obramowanie w przypadku wybrania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), zwracając wartość niezerową, jeśli formant jest widoczny.  
  
##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode  
 Określa, czy przyciski pole edycji mają płaski.  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisków płaski; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie przyciski pole edycji mają płaski. Użyj [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) metodę, aby zmienić wygląd płaski aplikacji.  
  
##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand  
 Określa, czy przycisk przetwarza [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iNotifyCode`  
 Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli przycisk przetwarza `WM_COMMAND` wiadomości, lub `FALSE` aby wskazać, że komunikat musi być obsługiwane przez narzędzi nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę po zamiar wysłać [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości do okna nadrzędnego.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [EN_UPDATE](http://msdn.microsoft.com/library/windows/desktop/bb761687) powiadomień. Dla każdego pola edycji z tym samym Identyfikatorem polecenia, co ten obiekt ustawia jego tekst etykiety etykietę tekstową tego obiektu.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) przez skopiowanie właściwości kontrolki pola edycji w żadnych narzędzi, która ma ten sam identyfikator polecenia co ten obiekt. Ta metoda nie działają, jeśli nie pasek narzędzi nie ma kontrolkę pola edycji, która ma ten sam identyfikator polecenia co ten obiekt.  
  
 Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [CMFCToolBarsCustomizeDialog klasy](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do nowego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tworząc wewnętrznej `CEdit` obiektu.  
  
##  <a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Nieużywane.  
  
 [in]`bDelay`  
 Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) zwróciła wartość niezerową, jeśli wewnętrznej `CEdit` obiekt jest widoczny.  
  
##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor  
 Wywoływane przez platformę, obsługując narzędzi nadrzędnej `WM_CTLCOLOR` wiadomości.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in]`nCtlColor`  
 Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do pędzla globalne okna.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) przez ustawienie kolory tła i tekstu kontekstu urządzenia podanego tekstu globalnego i kolory tła, odpowiednio.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 Wywoływane przez platformę, gdy globalne czcionka została zmieniona.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionki formantu w tym globalnych czcionki.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove  
 Wywoływane przez platformę, gdy przesuwa narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), aktualizując pozycji wewnętrznego `CEdit` obiektu  
  
##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow  
 Wywoływane przez platformę, gdy przycisk jest widoczny, czy niewidoczne.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bShow`  
 Określa, czy przycisk jest widoczny. Jeśli ten parametr ma `TRUE`, ten przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) za pomocą wyświetlania przycisku, jeśli `bShow` jest `TRUE`. W przeciwnym razie ta metoda powoduje ukrycie przycisku.  
  
##  <a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iSize`  
 Nową szerokość przycisku w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślną implementację klasy [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), aktualizując rozmiar i położenie wewnętrznego `CEdit` obiektu.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip  
 Wywoływane przez platformę, gdy jego tekst etykietki narzędzia aktualizacji narzędzi nadrzędnego.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Nieużywane.  
  
 [in]`iButtonIndex`  
 Nieużywane.  
  
 [in]`wndToolTip`  
 Formant, który wyświetla tekst elementu tooltip.  
  
 [out]`str`  
 A `CString` obiekt, który odbiera tekst etykietki narzędzia zaktualizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) za pomocą wyświetlania tekst etykietki narzędzia, skojarzony z części edycji przycisku. Jeśli wewnętrznej `CEdit` obiekt jest `NULL` lub uchwyt okna `CEdit` obiektu nie będzie rozpoznawał istniejącego okna, ta metoda nie działa i zwraca `FALSE`.  
  
##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents  
 Ustawia tekst w polu tekstowym.  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] sContents`  
 Określa nowy tekst do ustawienia.  
  
##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll  
 Wyszukuje [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) obiekt, który zawiera polecenie o określonym identyfikatorze i ustawia określony tekst w jego pola tekstowego.  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Określa identyfikator polecenia kontroli, dla którego zostanie zmieniony tekst.  
  
 [in]`strContents`  
 Określa nowy tekst do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ustawiono tekst; Jeśli 0 `CMFCToolBarEditBoxButton` formantu o identyfikatorze podane polecenie nie istnieje.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID  
 Określa identyfikator zasobu menu skrótów, który jest skojarzony z przyciskiem.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator zasobu menu skrótów.  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa Identyfikatora zasobu do utworzenia menu skrótów po kliknięciu przycisku paska narzędzi.  
  
##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode  
 Określa wygląd płaski przycisków pola edycji w aplikacji.  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bFlat`  
 Płaski przycisków pola edycji. Jeśli ten parametr ma `TRUE`, płaski wygląd jest włączone; w przeciwnym razie płaski wygląd jest wyłączony.  
  
### <a name="remarks"></a>Uwagi  
 Płaski domyślna w przypadku przycisków, pole edycji jest `TRUE`. Użyj [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) metoda pobierania płaski wygląd aplikacji.  
  
##  <a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle  
 Określa styl pasek narzędzi edycji kontrolki pola.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nStyle`  
 Nowy styl można ustawić.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) do `nStyle` także program wyłącza pola tekstowego, gdy aplikacja jest w trybie Dostosuj i włączy ją, gdy aplikacja nie jest w trybie Dostosuj (zobacz [CMFCToolBar: : SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) i [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md) listę styl prawidłowe flagi.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



