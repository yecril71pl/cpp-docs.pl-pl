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
ms.openlocfilehash: 7e6abf906d9fa0e5866b28a0c617e68edead8378
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852253"
---
# <a name="cminiframewnd-class"></a>Klasa CMiniFrameWnd
Przedstawia okna ramki w połowie wysokości zwykle widoczne wokół przestawnych pasków narzędzi.  
  
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
|[CMiniFrameWnd::Create](#create)|Tworzy `CMiniFrameWnd` obiektu po konstrukcji.|  
|[CMiniFrameWnd::CreateEx](#createex)|Tworzy `CMiniFrameWnd` obiektu (z dodatkowymi opcjami) po konstrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Te okna mini ramki zachowują się jak normalne ramki okien, z tą różnicą, że nie masz Maksymalizuj/Minimalizuj przycisków lub menu i muszą tylko jednym kliknięciem w menu systemu, aby je odrzucić.  
  
 Aby użyć `CMiniFrameWnd` obiektu, należy najpierw zdefiniować obiekt. Następnie wywołaj [Utwórz](#create) funkcja elementu członkowskiego, aby wyświetlić okno mini ramki.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia `CMiniFrameWnd` obiektów, zobacz artykuł [dokowanie i przestawne paski narzędzi](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd  
 Konstruuje `CMiniFrameWnd` obiektu, ale nie tworzy okno.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć okno, wywołaj [CMiniFrameWnd::Create](#create).  
  
##  <a name="create"></a>  CMiniFrameWnd::Create  
 Tworzy okno mini ramki Windows i dołącza je do `CMiniFrameWnd` obiektu.  
  
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
 Wskazuje ciąg znaków zakończony znakiem null, że nazwy klas Windows. Nazwa klasy może być dowolna nazwa, zarejestrowany w globalnej [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcji. Jeśli ma wartość NULL, zostanie zarejestrowana klasy okna dla Ciebie przez platformę. MFC udostępnia domyślną klasę następujące stylów i atrybuty:  
  
-   Ustawia styl bit CS_DBLCLKS, które wysyła kliknij dwukrotnie wiadomości do procedury okna, gdy użytkownik kliknie dwukrotnie myszy.  
  
-   Ustawia styl bitów CS_HREDRAW i CS_VREDRAW, które nakazują zawartość obszaru klienta, który ma zostać narysowany ponownie podczas okna zmienia rozmiar.  
  
-   Ustawia kursor klasy IDC_ARROW standardowa Windows.  
  
-   Ustawia pędzel tła klasy na wartość NULL, więc okna nie spowoduje to wymazanie tłem.  
  
-   Ikona logo Windows standard, którzy wymachują flagi ustawia ikonę klasy.  
  
-   Ustawia domyślny rozmiar i położenie okna, wskazane przez Windows.  
  
 *lpWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.  
  
 *dwStyle*  
 Określa atrybuty stylu okna. Obejmują one style standardowego okna i co najmniej jeden z następujących stylów specjalne:  
  
- MFS_MOVEFRAME umożliwia okna mini ramki, który ma zostać przeniesiona przez kliknięcie dowolnej krawędzi okna, a nie tylko podpis.  
  
- Wyłącza MFS_4THICKFRAME zmiany rozmiaru okna mini ramki.  
  
- MFS_SYNCACTIVE synchronizuje aktywacji okna mini ramki aktywacji okna nadrzędnego.  
  
- Umożliwia MFS_THICKFRAME Zezwalaj na rozmiar można zmieniać tak małej, jak zawartość obszaru klienckiego okna mini ramki.  
  
- Wyłącza MFS_BLOCKSYSMENU dostęp do menu systemowego i menu kontroli i konwertuje je na część podpisu (paska tytułu).  
  
 Zobacz [CWnd::Create](../../mfc/reference/cwnd-class.md#create) opis okna możliwych wartości stylu. Typowe połączenie używane dla systemu windows mini ramki jest WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.  
  
 *Rect*  
 A `RECT` struktury, określając żądane wymiary okna.  
  
 *pParentWnd*  
 Wskazuje okna nadrzędnego. Użyj wartości NULL dla okien najwyższego poziomu.  
  
 *nID*  
 Jeśli okno mini ramki jest tworzony jako okna podrzędnego, jest to identyfikator kontrolki podrzędnej; w przeciwnym razie 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Create` Inicjuje nazwy klasy okna i okna, a następnie rejestruje wartości domyślne dla jego stylu i element nadrzędny.  
  
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
 Określa styl rozszerzonej `CMiniFrameWnd` tworzona. Zastosowania któregokolwiek z [rozszerzone Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.  
  
 *lpClassName*  
 Wskazuje ciąg znaków zakończony znakiem null, że nazwy klas Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury). Nazwa klasy może być dowolna nazwa, zarejestrowany w globalnej [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcji lub żadnej z nazw wstępnie zdefiniowanych klasy kontrolki. Nie może być równa NULL.  
  
 *lpWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.  
  
 *dwStyle*  
 Określa atrybuty stylu okna. Zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CWnd::Create](../../mfc/reference/cwnd-class.md#create) opis możliwych wartości.  
  
 *Rect*  
 Rozmiar i położenie okna w współrzędne klienta *pParentWnd*.  
  
 *pParentWnd*  
 Wskazuje obiekt okna nadrzędnego.  
  
 *nID*  
 Identyfikator okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CreateEx` Parametry określają WNDCLASS, styl okna i (opcjonalnie) początkowe położenie i rozmiar okna. `CreateEx` Określa również okna nadrzędnego (jeśli istnieje) i identyfikator.  
  
 Gdy `CreateEx` wykonuje Windows wysyła [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) Komunikaty wyjściowe do okna.  
  
 Aby rozszerzyć domyślnej obsługi komunikatów, należy wyprowadzić klasę z `CMiniFrameWnd`, Dodaj mapy komunikatów do nowej klasy i zapewnić funkcji elementów członkowskich dla powyższych wiadomości. Zastąp `OnCreate`, na przykład do przeprowadzenia wymaganych inicjowania dla nowej klasy.  
  
 Zastąp dalsze `On` *komunikat* komunikatu obsługi będzie dodawał kolejne funkcje do klasy pochodnej.  
  
 Jeśli zostanie określony styl WS_VISIBLE, Windows wysyła okna wszystkie komunikaty, które są wymagane do aktywowania i wyświetlenie okna. Jeśli styl okna określa pasek tytułu, tytuł okna wskazywany przez *lpszWindowName* parametru jest wyświetlana na pasku tytułu.  
  
 *DwStyle* parametr może być dowolną kombinacją [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 Okna przybornika palety stary styl nie są już obsługiwane. Stary styl nie miał przycisk "X" Zamknij, było obsługiwane, podczas uruchamiania aplikacji MFC w poprzednich wersjach systemu Windows, ale nie jest już obsługiwana w programie Visual C++ .NET. Obsługiwana jest tylko nowy styl WS_EX_TOOLWINDOW; Aby uzyskać opis ten styl, zobacz [rozszerzone Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
