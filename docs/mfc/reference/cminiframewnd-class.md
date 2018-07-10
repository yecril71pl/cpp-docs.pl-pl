---
title: Klasa CMiniFrameWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 766faaa50e4efead96ff72c67aee71fec2386b18
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038589"
---
# <a name="cminiframewnd-class"></a>Klasa CMiniFrameWnd
Reprezentuje okno ramowe wysokości, zazwyczaj występuje wokół przestawne paski narzędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Konstruuje `CMiniFrameWnd` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|Tworzy `CMiniFrameWnd` obiektu po wykonaniu konstrukcji.|  
|[CMiniFrameWnd::CreateEx](#createex)|Tworzy `CMiniFrameWnd` obiektu (dodatkowe opcje) po wykonaniu konstrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Tych okien ramowych mini przypominają okien ramowych normalne, z wyjątkiem tego, że nie mają przyciski Minimalizuj/Maksymalizuj lub menu i można mieć tylko na jednym kliknięciem w menu systemu, aby je odrzucić.  
  
 Aby użyć `CMiniFrameWnd` obiektów, najpierw zdefiniować obiektu. Następnie wywołaj [Utwórz](#create) funkcji członkowskiej, aby wyświetlić okno ramowe minimalnej.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia `CMiniFrameWnd` obiektów, zobacz artykuł [dokowanie i przestawne paski narzędzi](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd  
 Konstruuje `CMiniFrameWnd` obiekt, ale nie powoduje utworzenia okna.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć okno, należy wywołać [CMiniFrameWnd::Create](#create).  
  
##  <a name="create"></a>  CMiniFrameWnd::Create  
 Tworzy okno ramowe mini systemu Windows i dołącza go do `CMiniFrameWnd` obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpClassName*  
 Punkty na ciąg znaków zakończony znakiem null nazwy klasy systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowana w globalnej [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji. Jeśli **NULL**, klasę okna zostanie zarejestrowany dla Ciebie przez platformę. MFC udostępnia domyślną klasę następujące style i atrybuty:  
  
-   Ustawia styl bit **CS_DBLCLKS**, które wysyła kliknij dwukrotnie wiadomości do procedury okna, gdy użytkownik kliknie dwukrotnie myszy.  
  
-   Ustawia styl bitów **CS_HREDRAW** i **CS_VREDRAW**, który bezpośrednie zawartość obszaru klienckiego narysowania, gdy okno zmienia rozmiar.  
  
-   Ustawia kursor klasy dla standardowego Windows **IDC_ARROW**.  
  
-   Ustawia pędzel tła klasy **NULL**, więc okna nie spowoduje usunięcie jego tła.  
  
-   Ustawia ikonę klasy na standardowy, Flaga wymachują ikonę logo systemu Windows.  
  
-   Ustawia okno domyślny rozmiar i położenie wskazywany przez system Windows.  
  
 *lpWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.  
  
 *dwStyle*  
 Określa atrybuty stylu okna. Obejmują one Style okna standardowej i co najmniej jeden z następujących stylów specjalne:  
  
- **MFS_MOVEFRAME** umożliwia mini ramkę okna do przeniesienia, klikając na dowolnej krawędzi okna, a nie tylko podpis.  
  
- **MFS_4THICKFRAME** wyłącza możliwość zmiany rozmiaru okna mini ramki.  
  
- **MFS_SYNCACTIVE** synchronizuje Aktywacja mini ramkę okna do aktywacji okna nadrzędnego.  
  
- **MFS_THICKFRAME** umożliwia okno ramowe mini być ustalone pomniejszonego Zezwalaj zawartość obszaru klienckiego.  
  
- **MFS_BLOCKSYSMENU** wyłącza dostęp do menu systemowym i w menu sterowania i konwertuje je na część podpisu (paska tytułu).  
  
 Zobacz [CWnd::Create](../../mfc/reference/cwnd-class.md#create) opis okna możliwych wartości stylu. Typowy kombinacja używany dla okien ramowych mini jest **ws_popup —&#124;ws_caption —&#124;ws_sysmenu —**.  
  
 *Rect*  
 A `RECT` struktury, określając odpowiednią wymiary okna.  
  
 *pParentWnd*  
 Wskazuje okno nadrzędne. Użyj **NULL** dla systemu windows najwyższego poziomu.  
  
 *nID*  
 Jeśli okno ramowe mini został utworzony jako okna podrzędnego, jest to identyfikator kontrolki podrzędnej; w przeciwnym razie 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** inicjuje nazwę klasy okna i nazwa okna i rejestruje wartości domyślne dla styl i nadrzędnej.  
  
##  <a name="createex"></a>  CMiniFrameWnd::CreateEx  
 Tworzy `CMiniFrameWnd` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Określa styl rozszerzonej `CMiniFrameWnd` tworzona. Zastosuj wszelkie z [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.  
  
 *lpClassName*  
 Wskazuje na ciąg znaków zakończony znakiem null nazwy klasy systemu Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury). Nazwa klasy może być dowolną nazwą zarejestrowana w globalnej [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji lub żadnej z nazw wstępnie zdefiniowane klasy formantu. Nie może być **NULL**.  
  
 *lpWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.  
  
 *dwStyle*  
 Określa atrybuty stylu okna. Zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CWnd::Create](../../mfc/reference/cwnd-class.md#create) opis możliwych wartości.  
  
 *Rect*  
 Rozmiar i położenie okna w współrzędne klienta *pParentWnd*.  
  
 *pParentWnd*  
 Wskazuje obiektu okna nadrzędnego.  
  
 *nID*  
 Identyfikator okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `CreateEx` Parametry określają **WNDCLASS**, styl okna i (opcjonalnie) początkowe położenie i rozmiar okna. `CreateEx` Określa również okna nadrzędnego (jeśli istnieje) i identyfikator.  
  
 Gdy `CreateEx` wykonuje system Windows wysyła [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) wiadomości do okna.  
  
 Aby rozszerzyć domyślnej obsługi wiadomości, klasa wyprowadzona z `CMiniFrameWnd`, Dodaj mapowanie komunikatów do nowej klasy i zapewnić funkcji Członkowskich powyżej komunikatów. Zastąpienie `OnCreate`, na przykład, aby wykonać wymagane inicjowania dla nowej klasy.  
  
 Zastąpienie dalsze **na *** komunikat* komunikatu programów obsługi, aby dodać dodatkowe funkcje do klasy pochodnej.  
  
 Jeśli **ws_visible —** podano stylu, system Windows wysyła okna wszystkie komunikaty, które są wymagane do aktywowania i wyświetlenie okna. Jeśli styl okna określa paska tytułu, tytuł okna wskazywana przez *lpszWindowName* parametru jest wyświetlany w pasku tytułu.  
  
 *DwStyle* parametr może być dowolną kombinacją [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 Stary windows przybornika palety stylu nie są już obsługiwane. Stary styl, który nie ma przycisku Zamknij "X", jest obsługiwana podczas działania aplikacji MFC w poprzednich wersjach systemu Windows, ale nie jest już obsługiwana w programie Visual C++ .NET. Tylko nowe `WS_EX_TOOLWINDOW` styl jest teraz obsługiwana; opis tego stylu, zobacz [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
## <a name="see-also"></a>Zobacz też  
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
