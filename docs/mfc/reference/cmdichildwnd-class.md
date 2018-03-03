---
title: "Cmdichildwnd — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: deca38c7c1fdaf9523e4186b801e5ed25042e46e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmdichildwnd-class"></a>Cmdichildwnd — klasa
Udostępnia funkcje systemu Windows wiele okien podrzędnych interfejsu (MDI) dokumentu, wraz z elementów członkowskich do zarządzania okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Konstruuje `CMDIChildWnd` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|Tworzy okno podrzędne systemu Windows MDI powiązane z `CMDIChildWnd` obiektu.|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Zwraca element nadrzędny MDI ramki okna MDI klienta.|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktywuje tego okna podrzędnego MDI.|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Niszczy tego okna podrzędnego MDI.|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maksymalizuje tego okna podrzędnego MDI.|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|Przywraca okno podrzędne MDI od rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.|  
|[CMDIChildWnd::SetHandles](#sethandles)|Ustawia uchwytów dla zasobów i menu skrótów.|  
  
## <a name="remarks"></a>Uwagi  
 Okna podrzędnego MDI wygląda podobnie okno ramowe typowe z tą różnicą, że wewnątrz ramki okna MDI, a nie na pulpicie zostanie wyświetlone okno podrzędne MDI. Okna podrzędnego MDI nie ma własnego paska menu, ale zamiast tego udostępnia menu ramkę okna MDI. Platformę automatycznie zmienia MDI menu ramki do reprezentowania aktywnego okna podrzędnego MDI.  
  
 Aby utworzyć użyteczne okna podrzędnego MDI aplikacji, klasa wyprowadzona z `CMDIChildWnd`. Zmienne Członkowskie dodawać do klasy pochodnej w celu przechowywania danych specyficzne dla aplikacji. Funkcje Członkowskie Implementowanie obsługi wiadomości i wiadomości są mapowane w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.  
  
 Istnieją trzy sposoby tworzenia okna podrzędnego MDI:  
  
-   Bezpośrednio utworzyć za pomocą **Utwórz**.  
  
-   Bezpośrednio utworzyć za pomocą `LoadFrame`.  
  
-   Pośrednio utworzenia go za pomocą szablonu dokumentu.  
  
 Przed wywołaniem **Utwórz** lub `LoadFrame`, należy tworzyć obiektu okno ramowe na stercie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem **Utwórz** można również zarejestrować klasy okna z [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej do ustawiania ikony, jak i klasy stylów ramki.  
  
 Użyj **Utwórz** funkcji członkowskiej do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.  
  
 `LoadFrame`wymaga mniejszej liczby argumentów niż **Utwórz**, a zamiast tego pobiera większość jego wartości domyślnej z zasobów, w tym ramki podpis, ikona tabeli akceleratora i menu. Aby mieć dostęp `LoadFrame`, te zasoby muszą mieć ten sam identyfikator zasobów (na przykład **IDR_MAINFRAME**).  
  
 Gdy `CMDIChildWnd` obiektu zawiera widoki i dokumentów, są tworzone pośrednio przez platformę, a nie bezpośrednio przez programistę. `CDocTemplate` Obiektu organizuje tworzenia ramki, tworzenie widoków zawierających i połączenie widoki dokument. Parametry `CDocTemplate` Określ konstruktora `CRuntimeClass` trzech klas zaangażowana (dokument, ramki i widoku). A `CRuntimeClass` obiekt jest używany przez platformę w celu dynamicznego tworzenia nowych ramek, gdy został określony przez użytkownika (na przykład przy użyciu polecenia nowy plik lub nowego okna MDI polecenia).  
  
 Pochodne klasy okien ramowych `CMDIChildWnd` musi być zadeklarowany ze `DECLARE_DYNCREATE` w kolejności dla powyższych `RUNTIME_CLASS` mechanizmu działała prawidłowo.  
  
 `CMDIChildWnd` Klasa dziedziczy znacznie jego domyślna implementacja z `CFrameWnd`. Aby uzyskać szczegółową listę tych funkcji, zapoznaj się [cframewnd —](../../mfc/reference/cframewnd-class.md) klasy opis. `CMDIChildWnd` Klasa ma następujące dodatkowe funkcje:  
  
-   W połączeniu z `CMultiDocTemplate` klasy, wiele `CMDIChildWnd` obiekty z tego samego szablonu dokumentu współużytkują tego samego menu zapisywania zasobów systemu Windows.  
  
-   Aktywne menu okna podrzędnego MDI całkowicie zastępuje menu Okno ramowe MDI i podpis aktywnego okna podrzędnego MDI zostanie dodany do podpisu okno ramowe MDI. Dalsze przykłady funkcji okna podrzędnego MDI wdrożonych w połączeniu z ramki okna MDI znaleźć `CMDIFrameWnd` klasy opis.  
  
 Nie należy używać języka C++ **usunąć** operatora, aby zniszczyć okno ramowe. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacja `PostNcDestroy` spowoduje usunięcie obiektu języka C++, gdy okno zostanie zniszczone. Gdy użytkownik zamyka okno ramowe domyślnie `OnClose` wywoła obsługi `DestroyWindow`.  
  
 Aby uzyskać więcej informacji na temat `CMDIChildWnd`, zobacz [okien ramowych](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd  
 Wywołanie do skonstruowania `CMDIChildWnd` obiektu.  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **Utwórz** można utworzyć okna widoczne.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMDIChildWnd::Create](#create).  
  
##  <a name="create"></a>CMDIChildWnd::Create  
 Wywołanie tej funkcji Członkowskich tworzenia okna podrzędnego MDI systemu Windows i dołączenie go do `CMDIChildWnd` obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CMDIFrameWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 Wskazuje na ciąg znaków zakończony znakiem null nazwy klasy systemu Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury). Nazwa klasy może być dowolną nazwą zarejestrowany [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej. Powinien być **NULL** dla standardowej `CMDIChildWnd`.  
  
 `lpszWindowName`  
 Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używane jako tekst paska tytułu.  
  
 `dwStyle`  
 Określa okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów. **Ws_child —** styl jest wymagana.  
  
 `rect`  
 Zawiera rozmiar i położenie okna. `rectDefault` Wartość umożliwia systemu Windows określić rozmiar i położenie nowej `CMDIChildWnd`.  
  
 `pParentWnd`  
 Określa okna nadrzędnego. Jeśli **NULL**, jest używany w głównym oknie aplikacji.  
  
 `pContext`  
 Określa [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aktualnie aktywne okno ramowe podrzędnych MDI można określić podpis ramkę okna nadrzędnego. Ta funkcja jest wyłączona, wyłączając **fws_addtotitle —** bit stylu ramki okna podrzędnego.  
  
 Struktura wywołuje tej funkcji Członkowskich w odpowiedzi na polecenie użytkownika można utworzyć okna podrzędnego i używa w ramach `pContext` parametru nawiązać prawidłowo okno podrzędne aplikacji. Podczas wywoływania **Utwórz**, `pContext` może być **NULL**.  
  
### <a name="example"></a>Przykład  
 Przykład 1:  
  
 [!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>Przykład  
 Przykład 2:  
  
 [!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame  
 Wywołanie tej funkcji, aby zwrócić ramka nadrzędny MDI.  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nadrzędnego okna MDI ramki.  
  
### <a name="remarks"></a>Uwagi  
 Ramka, zwracana jest dwóch elementów nadrzędnych usunięte z `CMDIChildWnd` i jest elementem nadrzędnym okna typu **MDICLIENT** który zarządza `CMDIChildWnd` obiektu. Wywołanie [GetParent](../../mfc/reference/cwnd-class.md#getparent) funkcji członkowskiej do zwrócenia `CMDIChildWnd` obiekt do natychmiastowego **MDICLIENT** nadrzędnego jako tymczasowej `CWnd` wskaźnika.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).  
  
##  <a name="mdiactivate"></a>CMDIChildWnd::MDIActivate  
 Wywołanie tej funkcji członkowskich można aktywować niezależnie od ramkę okna MDI okna podrzędnego MDI.  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas aktywowania ramki okna podrzędnego, który ostatnio uaktywniono również zostanie uaktywniona.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).  
  
##  <a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy  
 Wywołanie tej funkcji członkowskich można zniszczyć okna podrzędnego MDI.  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa tytuł okna podrzędnego z okno ramowe i dezaktywuje okna podrzędnego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize  
 Wywołanie tej funkcji Członkowskich, aby zmaksymalizować okna podrzędnego MDI.  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>Uwagi  
 Maksymalizacji okna podrzędnego zmienia rozmiar systemu Windows, aby wypełnił obszar kliencki okno ramowe obszaru klienckiego. System Windows umieszcza menu sterowania okna podrzędnego na pasku menu ramki tak, aby użytkownik może przywrócić lub zamknij okno podrzędne i dodaje tytuł okna podrzędnego do tytułu okna ramowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="mdirestore"></a>CMDIChildWnd::MDIRestore  
 Wywołanie tej funkcji Członkowskich do przywrócenia od rozmiaru w trybie zmaksymalizowanym lub zminimalizowanego okna podrzędnego MDI.  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="sethandles"></a>CMDIChildWnd::SetHandles  
 Ustawia uchwytów dla zasobów i menu skrótów.  
  
```  
void SetHandles(
    HMENU hMenu,  
    HACCEL hAccel);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Dojście zasobów menu.  
  
 `hAccel`  
 Dojście zasobów akceleratora.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić menu i akceleratora zasoby używane przez obiekt okna podrzędnego MDI.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Przykładowe MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)
