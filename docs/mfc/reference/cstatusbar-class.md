---
title: Cstatusbar — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb5fb6b09ba6d27828c9f76a1b2ee21323197f6b
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122944"
---
# <a name="cstatusbar-class"></a>Cstatusbar — klasa
Pasek sterowania z wiersza tekstu wyjściowego okienka lub "wskaźników."  
  
## <a name="syntax"></a>Składnia  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|Konstruuje `CStatusBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|Pobiera indeks danego wskaźnika identyfikatora.|  
|[CStatusBar::Create](#create)|Tworzy pasek stanu, dołącza go do `CStatusBar` obiektu i Ustawia wysokość początkowego czcionkę i paska.|  
|[CStatusBar::CreateEx](#createex)|Tworzy `CStatusBar` obiektu o dodatkowe style osadzonego `CStatusBarCtrl` obiektu.|  
|[CStatusBar::DrawItem](#drawitem)|Wywoływane, gdy visual aspekt zmiany formantu paska stanu rysowania przez właściciela.|  
|[CStatusBar::GetItemID](#getitemid)|Pobiera identyfikator wskaźnika dla danego indeksu.|  
|[CStatusBar::GetItemRect](#getitemrect)|Pobiera wyświetlane prostokąt dla danego indeksu.|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Pobiera identyfikator wskaźnika, stylu i szerokości dla danego indeksu.|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|Pobiera styl wskaźnika dla danego indeksu.|  
|[CStatusBar::GetPaneText](#getpanetext)|Pobiera tekst wskaźnika dla danego indeksu.|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umożliwia bezpośredni dostęp do podstawowych formant.|  
|[CStatusBar::SetIndicators](#setindicators)|Ustawia wskaźnik identyfikatorów.|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Ustawia identyfikator wskaźnika, stylu i szerokości dla danego indeksu.|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|Ustawia styl wskaźnika dla danego indeksu.|  
|[CStatusBar::SetPaneText](#setpanetext)|Ustawia tekst wskaźnika dla danego indeksu.|  
  
## <a name="remarks"></a>Uwagi  
 Okienka wyjściowego często służą jako wiersze komunikat, a wskaźniki stanu. Przykładami krótko opisano wybrane polecenie Wiersze komunikat pomocy menu i wskaźników określenia stanu blokady PRZEWIJANIA, NUM LOCK i kluczy.  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), funkcji członkowskiej nowych 4.0 MFC umożliwia skorzystać z obsługi systemu Windows formantu wspólnego stanu paska dostosowania i dodatkowe funkcje. `CStatusBar` Funkcje Członkowskie zapewniają większość funkcjonalności formanty standardowe systemu Windows; Jednak jeśli wywołasz `GetStatusBarCtrl`, z paskami stanu można nadać jeszcze więcej właściwości paska stanu Windows 95/98. Podczas wywoływania `GetStatusBarCtrl`, zwróci odwołanie do `CStatusBarCtrl` obiektu. Zobacz [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) uzyskać więcej informacji o projektowaniu paski narzędzi przy użyciu formanty standardowe systemu Windows. Więcej ogólnych informacji na temat typowych formantów, zobacz [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493) w zestawie Windows SDK.  
  
 Platformę przechowuje informacje wskaźnika w tablicy z lewej strony wskaźnika na pozycji 0. Podczas tworzenia paska stanu, możesz użyć tablica ciągów identyfikatorów, które kojarzy platformę z odpowiednich wskaźników. Następnie można identyfikator ciągu lub indeksu dostępu wskaźnika.  
  
 Domyślnie pierwszy wskaźnika jest "elastyczne": zajmuje on długość paska stanu nie są używane przez inne okienka wskaźnika, tak aby były inne okienka wyrównany do prawej.  
  
 Aby utworzyć paska stanu, wykonaj następujące kroki:  
  
1.  Utworzyć `CStatusBar` obiektu.  
  
2.  Wywołanie [Utwórz](#create) (lub [CreateEx](#createex)) funkcja tworzenia paska stanu okna i dołączenie go do `CStatusBar` obiektu.  
  
3.  Wywołanie [SetIndicators](#setindicators) do skojarzenia identyfikator ciągu z każdego wskaźnika.  
  
 Istnieją trzy sposoby aktualizowana tekstu w okienku paska stanu:  
  
1.  Wywołanie [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) do zaktualizowania tekstu w okienku tylko 0.  
  
2.  Wywołanie [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) w obsłudze on_update_command_ui — pasek stanu.  
  
3.  Wywołanie [SetPaneText](#setpanetext) do zaktualizowania tekstu dla dowolnego okienka.  
  
 Wywołanie [SetPaneStyle](#setpanestyle) aktualizacji stylu okienku paska stanu.  
  
 Aby uzyskać więcej informacji na temat używania `CStatusBar`, zapoznaj się z artykułem [implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [techniczna 31 Uwaga: paski sterowania](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar —](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex  
 Pobiera indeks wskaźnika dla podanego identyfikatora.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIDFind*  
 Identyfikator ciągu wskaźnika, którego indeks ma być pobrana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wskaźnika w przypadku powodzenia; -1, jeśli nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Indeks pierwszego wskaźnika jest 0.  
  
##  <a name="create"></a>  CStatusBar::Create  
 Stan paska (okno podrzędne) tworzy i kojarzy ją z `CStatusBar` obiektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, którego okna systemu Windows jest nadrzędny paska stanu.  
  
 *dwStyle*  
 Style paska stanu. Oprócz standardowych systemu Windows [style](../../mfc/reference/styles-used-by-mfc.md#window-styles), te style są obsługiwane.  
  
- Pasek sterowania CBRS_TOP jest u góry okna ramowego.  
  
- Pasek sterowania CBRS_BOTTOM jest u dołu okna ramowego.  
  
- Pasek sterowania CBRS_NOALIGN nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.  
  
 *nID*  
 Identyfikator paska narzędzi okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ponadto ustawia początkowej czcionki i ustawia stan wysokość paska wartość domyślna.  
  
##  <a name="createex"></a>  CStatusBar::CreateEx  
 Wywołanie tej funkcji, aby utworzyć stanu paska (okno podrzędne) i skojarz ją z `CStatusBar` obiektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, którego okna systemu Windows jest nadrzędny paska stanu.  
  
 *dwCtrlStyle*  
 Dodatkowe style w celu utworzenia osadzonego [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) obiektu. Domyślnie określa pasek stanu bez uchwyt zmiany rozmiaru lub etykietka narzędzia obsługi. Style paska stanu, obsługiwane są następujące:  
  
- SBARS_SIZEGRIP formantu paska stanu obejmuje uchwyt zmiany rozmiaru na prawym końcu paska stanu. Uchwyt zmiany rozmiaru jest podobny do rozmiaru obramowanie; jest prostokątny obszar, który użytkownik może kliknij i przeciągnij, aby zmienić rozmiar okna nadrzędnego.  
  
- Pasek stanu SBT_TOOLTIPS obsługuje etykietki.  
  
 Aby uzyskać więcej informacji o tych stylów, zobacz [ustawienia formantu CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).  
  
 *dwStyle*  
 Style paska stanu. Wartość domyślna Określa utworzony pasek stanu widoczne w dolnej części okna ramowe. Zastosuj dowolną kombinację pasek stylów formantu na liście stanu [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Jednak ten parametr powinien zawsze należy uwzględniać ws_child — i ws_visible — style.  
  
 *nID*  
 Identyfikator okna podrzędnego na pasku stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja także ustawia czcionkę początkowej i ustawia stan wysokość paska wartość domyślna.  
  
 Użyj `CreateEx`, zamiast [Utwórz](#create)w przypadku niektórych style musi być obecny podczas tworzenia formantu paska stanu osadzonych. Na przykład ustawić *dwCtrlStyle* do SBT_TOOLTIPS do wyświetlenia etykietki narzędzi w obiekcie paska stanu.  
  
##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar  
 Konstruuje `CStatusBar` obiekt, tworzy domyślną czcionkę paska stanu w razie potrzeby i ustawia charakterystyki czcionki do wartości domyślnych.  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>  CStatusBar::DrawItem  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy visual aspekt zmiany paska stanu rysowanych przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Wskaźnik do [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 `itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CStatusBar` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w *lpDrawItemStruct* przed zakończeniem tej funkcji Członkowskich.  
  
##  <a name="getitemid"></a>  CStatusBar::GetItemID  
 Zwraca identyfikator określony przez wskaźnik *nIndex*.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks wskaźnika o identyfikatorze ma być pobrana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator określony przez wskaźnik *nIndex*.  
  
##  <a name="getitemrect"></a>  CStatusBar::GetItemRect  
 Kopiuje współrzędnych wskaźnika określony przez *nIndex* w strukturze wskazywana przez *lprect —*.  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks wskaźnika współrzędnych prostokąta, których mają zostać pobrane.  
  
 *lprect —*  
 Wskazuje [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który otrzyma współrzędnych wskaźnika określony przez *nIndex*.  
  
### <a name="remarks"></a>Uwagi  
 Współrzędne są podawane w pikselach względem lewego górnego rogu paska stanu.  
  
##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo  
 Ustawia *nID*, *nStyle*, i *cxWidth* do Identyfikatora, stylu i szerokości panelu wskaźnika w lokalizacji określonej przez *nIndex*.  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks okienka, którego informacje ma być pobrana.  
  
 *nID*  
 Odwołanie do Unit ustawiony na identyfikator okienka.  
  
 *nStyle*  
 Odwołanie do Unit ustawionym Styl okienka.  
  
 *cxWidth*  
 Odwołanie do liczba całkowita, która ma ustawioną wartość szerokość panelu.  
  
##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle  
 Wywołanie tej funkcji Członkowskich pobrać styl okienku paska stanu.  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks okienka, którego styl ma być pobrana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Styl w okienku paska stanu określonego przez *nIndex*.  
  
### <a name="remarks"></a>Uwagi  
 Styl okienka Określa, jak okienku zostanie wyświetlona.  
  
 Aby uzyskać listę style dostępne na paskach stanu, zobacz [Utwórz](#create).  
  
##  <a name="getpanetext"></a>  CStatusBar::GetPaneText  
 Wywołanie tej funkcji Członkowskich pobrać tekst wyświetlany w okienku paska stanu.  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks okienko tekstu, którego ma być pobrana.  
  
 *rString*  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający tekst, który ma zostać pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt zawierający okienko tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Drugi formularz tego elementu członkowskiego funkcji wypełnienia `CString` obiekt z ciągu tekstowego.  
  
##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl  
 Ta funkcja członkowska umożliwia bezpośredni dostęp do podstawowych formant.  
  
```  
CStatusBarCtrl& GetStatusBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawiera odwołanie do [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `GetStatusBarCtrl` korzystanie z funkcji wspólnej formantu paska stanu systemu Windows i korzystać z obsługi [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) zapewnia dostosowywanie paska stanu. Na przykład za pomocą formantu wspólnego, można określić styl zawierający uchwyt zmiany rozmiaru, na pasku stanu, lub można określić styl pasek stanu są wyświetlane u góry obszaru klienckiego okna nadrzędnego.  
  
 Więcej ogólnych informacji na temat typowych formantów, zobacz [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493) w zestawie Windows SDK.  
  
##  <a name="setindicators"></a>  CStatusBar::SetIndicators  
 Ustawia identyfikator każdy wskaźnik do wartości określonej przez odpowiadający mu element w tablicy *lpIDArray*Ładuje określony przez każdy identyfikator zasobu ciągu i ustawia tekst wskaźnika do ciągu.  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lpIDArray*  
 Wskaźnik do tablicy identyfikatorów.  
  
 *nIDCount*  
 Liczba elementów w tablicy wskazywana przez *lpIDArray*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo  
 Ustawia okienko określony wskaźnik do nowego Identyfikatora, stylu i szerokości.  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks w okienku wskaźnika, którego styl ma być utworzony.  
  
 *nID*  
 Nowy identyfikator dla tego okienka wskaźnika.  
  
 *nStyle*  
 Styl nowego okienka wskaźnika.  
  
 *cxWidth*  
 Nową szerokość wskaźnika okienka.  
  
### <a name="remarks"></a>Uwagi  
 Obsługiwane są następujące style wskaźnika:  
  
- SBPS_NOBORDERS nr 3-obramowania wokół okienka.  
  
- Wycofaj SBPS_POPOUT obramowania tak, czy tekst "pojawia się."  
  
- Nie należy SBPS_DISABLED Rysowanie tekstu.  
  
- Okienko SBPS_STRETCH Stretch, aby wypełnić nieużywane miejsce. Tylko jedno okienko na pasku stanu może zawierać ten styl.  
  
- Nr SBPS_NORMAL stretch, obramowanie lub wyskakującego.  
  
##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle  
 Wywołanie funkcji członkowskiej na ustawienie stylu okienku paska stanu.  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks okienka, którego styl ma być utworzony.  
  
 *nStyle*  
 Styl okienka, którego styl ma być utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Styl okienka Określa, jak okienku zostanie wyświetlona.  
  
 Aby uzyskać listę style dostępne na paskach stanu, zobacz [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>  CStatusBar::SetPaneText  
 Wywołanie tej funkcji członkowskich można ustawić tekst okienko na ciąg wskazywana przez *lpszNewText*.  
  
```  
BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Indeks okienko tekstu, którego ma dotyczyć.  
  
 *lpszNewText*  
 Wskaźnik do nowego tekstu panelu.  
  
 *baktualizacji*  
 Jeśli PRAWDA, okienku jest unieważniona po ustawieniu tekst.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `SetPaneText`, należy dodać program obsługi aktualizacji interfejsu użytkownika można wyświetlić nowy tekst w pasku stanu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLBARS](../../visual-cpp-samples.md)   
 [DLGCBR32 próbki MFC](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cstatusbarctrl — klasa](../../mfc/reference/cstatusbarctrl-class.md)   
 [Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
