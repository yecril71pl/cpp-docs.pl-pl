---
title: Cmdiframewnd — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
dev_langs:
- C++
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb9f87ed5ae3027e7743a36c2484017d6381f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmdiframewnd-class"></a>Cmdiframewnd — klasa
Udostępnia funkcje systemu Windows wielu okno ramowe interfejsu (MDI) dokumentu, wraz z elementów członkowskich do zarządzania okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Konstruuje `CMDIFrameWnd`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|Tworzy Windows **MDICLIENT** okna dla tego `CMDIFrameWnd`. Wywoływane przez `OnCreate` funkcji członkowskiej klasy `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Tworzy nowe okno podrzędne.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Zwraca menu podręcznego okna.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktywuje innego okna podrzędnego MDI.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Rozmieszcza wszystkich okien podrzędnych w kaskadowego formacie.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Pobiera aktywnego okna podrzędnego MDI, wraz z Flaga wskazująca, czy obiekt podrzędny jest zmaksymalizowane.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Rozmieszcza wszystkich okien podrzędnych dokumentu w trybie zminimalizowanym.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maksymalizuje okno podrzędne MDI.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Aktywuje okna podrzędnego bezpośrednio za okno podrzędne aktualnie aktywny i umieszcza okno podrzędne aktualnie aktywny za wszystkie inne okna podrzędnego.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktywuje poprzedniego okna podrzędnego i umieszcza okno podrzędne aktualnie aktywne natychmiast za nią.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Przywraca okno podrzędne MDI od rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Zastępuje menu ramki okna MDI i/lub menu podręcznego okna.|  
|[CMDIFrameWnd::MDITile](#mditile)|Rozmieszcza wszystkie podrzędne w układzie sąsiadującym formacie.|  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć użyteczne MDI ramkę okna do aplikacji, pochodzi z klasy `CMDIFrameWnd`. Zmienne Członkowskie dodawać do klasy pochodnej w celu przechowywania danych specyficzne dla aplikacji. Funkcje Członkowskie Implementowanie obsługi wiadomości i wiadomości są mapowane w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.  
  
 Można utworzyć przez wywołanie metody ramki okna MDI [Utwórz](../../mfc/reference/cframewnd-class.md#create) lub [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) funkcji członkowskiej klasy `CFrameWnd`.  
  
 Przed wywołaniem **Utwórz** lub `LoadFrame`, musi konstruowania obiektu okno ramowe na stercie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem **Utwórz** można również zarejestrować klasy okna z [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej do ustawiania ikony, jak i klasy stylów ramki.  
  
 Użyj **Utwórz** funkcji członkowskiej do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.  
  
 `LoadFrame` wymaga mniejszej liczby argumentów niż **Utwórz**, a zamiast tego pobiera większość jego wartości domyślnej z zasobów, w tym ramki podpis, ikona tabeli akceleratora i menu. Dostępu do `LoadFrame`, te zasoby muszą mieć ten sam identyfikator zasobów (na przykład **IDR_MAINFRAME**).  
  
 Chociaż **MDIFrameWnd** jest pochodną `CFrameWnd`, pochodną klasy okna ramowe `CMDIFrameWnd` nie muszą być zadeklarowane z `DECLARE_DYNCREATE`.  
  
 `CMDIFrameWnd` Klasa dziedziczy znacznie jego domyślna implementacja z `CFrameWnd`. Aby uzyskać szczegółową listę tych funkcji, zapoznaj się [cframewnd —](../../mfc/reference/cframewnd-class.md) klasy opis. `CMDIFrameWnd` Klasa ma następujące dodatkowe funkcje:  
  
-   Zarządza ramki okna MDI **MDICLIENT** okna położenia go w połączeniu z paskami sterowania. Okno klienckie MDI jest bezpośrednią lokacją nadrzędną okien ramowych podrzędnych MDI. **Ws_hscroll —** i **ws_vscroll —** okna style określone na `CMDIFrameWnd` dotyczą okno klienckie MDI, a nie głównego okna ramowego, dlatego użytkownika mogą być przewijane w obszarze klienta MDI (jak systemu Windows Program Menedżer, na przykład).  
  
-   Okna ramowe MDI jest właścicielem menu domyślna, która służy jako pasek menu po nie aktywne okno podrzędne MDI. W przypadku aktywny formularz podrzędny MDI paska menu Okno ramowe MDI jest automatycznie zastępowane menu okna podrzędnego MDI.  
  
-   Ramka okna MDI działa w połączeniu z bieżącego okna podrzędnego MDI, jeśli istnieje. Na przykład komunikaty poleceń mają delegowane do aktywnego podrzędnego MDI przed ramkę okna MDI.  
  
-   Ramka okna MDI ma następujące standardowe polecenia menu okna obsługi domyślne:  
  
    - **ID_WINDOW_TILE_VERT —**  
  
    - **ID_WINDOW_TILE_HORZ —**  
  
    - **ID_WINDOW_CASCADE —**  
  
    - **ID_WINDOW_ARRANGE —**  
  
-   Ramka okna MDI ma również implementacja **id_window_new —**, co powoduje nowej ramki i widoku w bieżącym dokumencie. Aplikację można zastąpić te domyślnej implementacji polecenie, aby dostosować MDI okna obsługi.  
  
 Nie należy używać języka C++ **usunąć** operatora, aby zniszczyć okno ramowe. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacja `PostNcDestroy` spowoduje usunięcie obiektu języka C++, gdy okno zostanie zniszczone. Gdy użytkownik zamyka okno ramowe domyślnie `OnClose` wywoła obsługi `DestroyWindow`.  
  
 Aby uzyskać więcej informacji na temat `CMDIFrameWnd`, zobacz [okien ramowych](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd  
 Konstruuje `CMDIFrameWnd` obiektu.  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **Utwórz** lub `LoadFrame` funkcji członkowskiej, aby utworzyć okno ramowe widoczne MDI.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient  
 Tworzy okno klienckie MDI, która zarządza `CMDIChildWnd` obiektów.  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `lpCreateStruct`  
 Długie wskaźnik do [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) struktury.  
  
 `pWindowMenu`  
 Wskaźnik do menu podręcznego okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska powinna być wywoływana w razie przesłonięcia `OnCreate` funkcji członkowskiej bezpośrednio.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild  
 Tworzy nowe okno podrzędne.  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pClass`  
 Klasa czasu wykonywania okna podrzędnego, który ma zostać utworzony.  
  
 *nResource*  
 Identyfikator udostępnionego zasoby skojarzone z okna podrzędnego.  
  
 `hMenu`  
 Menu okna podrzędnego.  
  
 `hAccel`  
 Okno podrzędne akceleratora.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do tworzenia podrzędnych windows ramki okna MDI.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 W tym przykładzie jest fragment artykułu bazy wiedzy Q201045, "Porada: Dodawanie wielu typów okna do MDI Non-dokument/widok aplikacji." Artykuły bazy wiedzy są dostępne pod adresem [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 Wywołanie tej funkcji członkowskich można uzyskać dojścia do bieżącego menu podręcznego o nazwie "Windows" (menu wyskakującego z elementami menu MDI okna zarządzania).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Parametry  
 *hMenuBar*  
 Bieżący paska menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Menu podręcznego okna, jeśli istnieje; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja szuka menu podręczne zawierające standardowe polecenia menu okna, takich jak **id_window_new —** i **id_window_tile_horz —**.  
  
 Przesłonić tę funkcję elementu członkowskiego, jeśli masz menu okna, które nie są używane standardowe polecenie identyfikatorów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 Aktywuje innego okna podrzędnego MDI.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndActivate*  
 Wskazuje okna podrzędnego MDI aktywacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska wysyła [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) wiadomości do okna podrzędnego aktywowane i dezaktywowany okna podrzędnego.  
  
 Jest to ten sam komunikat, który jest wysyłany, jeśli użytkownik zmieni fokus do okna podrzędnego MDI za pomocą klawiatury lub myszy.  
  
> [!NOTE]
>  Okno podrzędne MDI aktywowano niezależnie od ramkę okna MDI. Podczas aktywowania ramki okna podrzędnego, który ostatnio uaktywniono są wysyłane [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) komunikat do rysowania ramki aktywne okno i pasek podpisu, ale nie otrzyma inny `WM_MDIACTIVATE` wiadomości.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 Rozmieszcza wszystkich okien podrzędnych MDI w formacie cascade.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 `nType`  
 Określa flagi cascade. Można określić tylko następujące flagi: `MDITILE_SKIPDISABLED`, który uniemożliwia trwa kaskadowy przez wyłączone okien podrzędnych MDI.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję `MDICascade`, bez parametrów, dokonuje kaskadowych wszystkich okien podrzędnych MDI, w tym wyłączone z nich. Druga wersja opcjonalnie nie nie cascade wyłączone okien podrzędnych MDI Jeśli określisz `MDITILE_SKIPDISABLED` dla `nType` parametru.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 Pobiera bieżący active MDI okna podrzędnego, wraz z flagę wskazującą, czy okno podrzędne jest zmaksymalizowane.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pbMaximized*  
 Wskaźnik do **BOOL** zwracają wartość. Ustaw **TRUE** przy powrocie czy okno jest zmaksymalizowane; w przeciwnym razie **FALSE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do aktywnego okna podrzędnego MDI.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 Rozmieszcza wszystkich okien podrzędnych dokumentu w trybie zminimalizowanym.  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie ma ona wpływu na okno podrzędne, które nie są zminimalizowane.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIFrameWnd::MDICascade](#mdicascade).  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 Maksymalizuje określonego okna podrzędnego MDI.  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskazuje okno, aby zmaksymalizować.  
  
### <a name="remarks"></a>Uwagi  
 Maksymalizacji okna podrzędnego zmienia rozmiar systemu Windows, aby Wypełnianie okna klienta obszaru klienckiego. Systemu Windows miejsc okna podrzędnego menu sterowania na pasku menu ramki, użytkownik może przywrócić lub zamknij okno podrzędne. Dodaje również tytuł okna podrzędnego do tytułu okna ramowego.  
  
 Jeśli inne okno podrzędne MDI aktywowaniu maksymalizacji aktywnego okna podrzędnego MDI systemu Windows przywraca podrzędne aktualnie aktywny i Maksymalizuje okno podrzędne nowo aktywowane.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 Aktywuje okna podrzędnego bezpośrednio za okno podrzędne aktualnie aktywny i umieszcza okno podrzędne aktualnie aktywny za wszystkie inne okna podrzędnego.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aktualnie aktywnego okna podrzędnego MDI jest zmaksymalizowane, funkcja członkowska przywraca podrzędne aktualnie aktywny i maksymalizację nowo aktywowanego podrzędnych.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 Aktywuje poprzedniego okna podrzędnego i umieszcza okno podrzędne aktualnie aktywne natychmiast za nią.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aktualnie aktywnego okna podrzędnego MDI jest zmaksymalizowane, funkcja członkowska przywraca podrzędne aktualnie aktywny i maksymalizację nowo aktywowanego podrzędnych.  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 Przywraca okno podrzędne MDI od rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskazuje okna do przywrócenia.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 Zastępuje menu ramki okna MDI i/lub menu podręcznego okna.  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *pFrameMenu*  
 Określa menu nowego menu okna ramowego. Jeśli **NULL**, menu nie zostanie zmieniona.  
  
 `pWindowMenu`  
 Określa menu nowego menu podręcznego okna. Jeśli **NULL**, menu nie zostanie zmieniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do menu okna ramowego zastąpione przez tę wiadomość. Wskaźnik mogą być tymczasowe i nie powinny być przechowywane do późniejszego użycia.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu `MDISetMenu`, aplikacja musi wywołać [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) funkcji członkowskiej klasy `CWnd` do aktualizacji paska menu.  
  
 Jeśli to wywołanie zastępuje menu podręcznego okna, elementy menu okna podrzędnego MDI zostaną usunięte z poprzednich menu okna i dodane do nowego menu podręcznego okna.  
  
 To wywołanie zastępuje menu ramki okna MDI okna podrzędnego MDI jest zmaksymalizowane, formanty formant menu i przywracania są usuwane z poprzedniego menu okna ramowego i dodane do nowego menu.  
  
 Nie należy wywoływać funkcji członkowskiej, jeśli używasz platformę do zarządzania okien podrzędnych MDI.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 Rozmieszcza wszystkie podrzędne w układzie sąsiadującym formacie.  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 `nType`  
 Określa flagi kafelków. Ten parametr może być jednym z następujących flag:  
  
- `MDITILE_HORIZONTAL` Kafelki okien podrzędnych MDI, że jedno okno pojawi się nad innym.  
  
- `MDITILE_SKIPDISABLED` Zapobiega rozmieszczany jest wyłączone okien podrzędnych MDI.  
  
- `MDITILE_VERTICAL` Kafelki okien podrzędnych MDI, że jedno okno jest wyświetlany obok innego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję `MDITile`, bez parametrów, Rozmieszcza okna sąsiadująco w pionie w systemie Windows w wersji 3.1 lub nowszej. Druga wersja Kafelki windows pionie lub poziomie, w zależności od wartości `nType` parametru.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Przykładowe MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
