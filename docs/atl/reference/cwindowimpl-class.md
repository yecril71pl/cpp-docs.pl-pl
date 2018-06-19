---
title: Klasa CWindowImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4884bbacd03675d00cb1a49b937265ab5faa2835
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366159"
---
# <a name="cwindowimpl-class"></a>Klasa CWindowImpl
Udostępnia metody do tworzenia lub Tworzenie podklasy okna.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Nowa klasa pochodzi od `CWindowImpl`.  
  
 *TBase*  
 Klasa podstawowa klasy. Domyślnie klasa podstawowa jest [CWindow](../../atl/reference/cwindow-class.md).  
  
 `TWinTraits`  
 A [klasa cech](../../atl/understanding-window-traits.md) definiuje styl okna. Wartość domyślna to `CControlWinTraits`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|Tworzy okno.|  
  
### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|Udostępnia domyślne przetwarzania komunikatów.|  
|[GetCurrentMessage](#getcurrentmessage)|Zwraca bieżący komunikat.|  
|[GetWindowProc](#getwindowproc)|Zwraca bieżącą procedurę okna.|  
|[OnFinalMessage](#onfinalmessage)|Metoda wywoływana po otrzymaniu ostatniego komunikatu (zazwyczaj `WM_NCDESTROY`).|  
|[SubclassWindow](#subclasswindow)|Podklasy okna.|  
|[UnsubclassWindow](#unsubclasswindow)|Przywraca uprzednio podklasą okna.|  
  
### <a name="static-methods"></a>Metody statyczne  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|Zwraca wystąpienie statyczne klasy [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), który zarządza informacjami klasy okna.|  
|[WindowProc](#windowproc)|Przetwarza wiadomości wysyłane do okna.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje klasę okna oryginalną procedurę okna.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `CWindowImpl` można utworzyć okna lub podklasa klasy istniejącego okna. `CWindowImpl` procedurę okna używa mapy komunikatów do kierowania wiadomości na odpowiednie programy obsługi.  
  
 `CWindowImpl::Create` Tworzy okno na podstawie informacji klasy okna, który jest zarządzany przez [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` zawiera [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra, co oznacza `CWndClassInfo` rejestruje nową klasę okna. Jeśli chcesz superklasie istniejącej klasy okna, pochodzi z klasy `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra. W takim przypadku `CWndClassInfo` rejestruje klasę okna, jest oparta na istniejącej klasy, która używa `CWindowImpl::WindowProc`. Na przykład:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Ponieważ `CWndClassInfo` zarządza informacjami dla tylko jednej klasy okna, każde okno został utworzony za pomocą wystąpienia `CWindowImpl` opiera się na tej samej klasy okna.  
  
 `CWindowImpl` obsługuje również podklasy okna. `SubclassWindow` Metody dołącza do istniejącego okna `CWindowImpl` obiektu i zmienia procedurę okna `CWindowImpl::WindowProc`. Każde wystąpienie `CWindowImpl` można podklasy innego okna.  
  
> [!NOTE]
>  Dla żadnej podanej `CWindowImpl` obiektu, albo wywoływać **Utwórz** lub `SubclassWindow`. Nie należy wywoływać obu metod dla tego samego obiektu.  
  
 Oprócz `CWindowImpl`, zapewnia ATL [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) można utworzyć okna, który jest zawarty w innym obiekcie.  
  
 Destruktor klasy podstawowej (~ **CWindowImplRoot**) zapewnia, że okno jest usunięty przed obiekt zostanie zniszczony.  
  
 `CWindowImpl` pochodną **CWindowImplBaseT**, co wynika ze **CWindowImplRoot**, co wynika ze **TBase** i [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Aby uzyskać więcej informacji dotyczących|Zobacz|  
|--------------------------------|---------|  
|Tworzenie formantów|[ALT — samouczek](../../atl/active-template-library-atl-tutorial.md)|  
|Przy użyciu systemu windows w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|  
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="create"></a>  CWindowImpl::Create  
 Tworzy okno oparte na nową klasę okna.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [in] Dojście do okna nadrzędnego lub właściciela.  
  
 `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) Struktura określająca położenie okna. `RECT` Mogą być przekazywane przez wskaźnik lub odwołanie.  
  
 `szWindowName`  
 [in] Określa nazwę okna. Wartość domyślna to **NULL**.  
  
 `dwStyle`  
 [in] Styl okna. Ta wartość jest połączona z styl podał klasa cech okna. Wartość domyślna zapewnia cechy klasy pełną kontrolę nad styl. Aby uzyskać listę możliwych wartości, zobacz [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie Windows SDK.  
  
 `dwExStyle`  
 [in] Styl okna rozszerzonej. Ta wartość jest połączona z styl podał klasa cech okna. Wartość domyślna zapewnia cechy klasy pełną kontrolę nad styl. Aby uzyskać listę możliwych wartości, zobacz [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `MenuOrID`  
 [in] Dla okna podrzędnego identyfikator okna. W ramach najwyższego poziomu okna, menu uchwyt okna. Wartość domyślna to **0U**.  
  
 `lpCreateParam`  
 [in] Wskaźnik do danych tworzenie okien. Aby uzyskać pełny opis, zobacz opis ostatni parametr, aby [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia dojścia do okna nowo utworzony. W przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** najpierw rejestruje klasę okna, jeśli nie została jeszcze zarejestrowana. Nowo utworzony okna są automatycznie dołączane do `CWindowImpl` obiektu.  
  
> [!NOTE]
>  Nie wywołuj **Utwórz** Jeśli już o nazwie [SubclassWindow](#subclasswindow).  
  
 Aby używać klasy okna, która jest oparta na istniejącej klasy okna, pochodzi z klasy `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra. Procedurę okna istniejącej klasy okna jest zapisywany w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) omówienie.  
  
> [!NOTE]
>  Jeśli 0 jest używany jako wartość `MenuOrID` parametru musi być określona jako 0U (wartość domyślna), aby uniknąć błędów kompilatora.  
  
##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc  
 Wywoływane przez [WindowProc](#windowproc) do przetwarzania komunikatów, które nie są obsługiwane przez mapy komunikatów.  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```  
  
### <a name="parameters"></a>Parametry  
 `uMsg`  
 [in] Komunikat wysyłany do okna.  
  
 `wParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `DefWindowProc` wywołania [CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) Win32/funkcja do wysyłania informacji wiadomości do procedury okna, określony w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
 Funkcja bez parametrów automatycznie pobiera wymagane parametry z bieżącego komunikatu.  
  
##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage  
 Zwraca bieżący komunikat w `MSG` struktury.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący komunikat.  
  
##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc  
 Zwraca `WindowProc`, bieżącą procedurę okna.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącą procedurę okna.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby zastąpić procedurę okna swoją własną.  
  
##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo  
 Wywoływane przez [Utwórz](#create) dostępu do informacji klasy okna.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Statyczne wystąpienia [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CWindowImpl` uzyskuje tej metody za pomocą [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra, która określa nowe klasy okna.  
  
 Aby superklasie istniejącej klasy okna, pochodzi z klasy `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra, aby zastąpić `GetWndClassInfo`. Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) omówienie.  
  
 Oprócz funkcji `DECLARE_WND_CLASS` i `DECLARE_WND_SUPERCLASS` makra, można zastąpić `GetWndClassInfo` z własną implementację.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc  
 W zależności od oknie wskazuje na jedną z poniższych procedur okna.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Uwagi  
  
|Typ okna|Procedury okna|  
|--------------------|----------------------|  
|Okno oparte na nową klasę okna, określony przez [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra.|[DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) funkcji Win32.|  
|Okno oparte na klasę okna, które modyfikuje istniejącej klasy, określonej za pomocą [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra.|Procedurę okna istniejącej klasy okna.|  
|Będące podklasami okna.|Okno podklasą oryginalną procedurę okna.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) wysyła komunikat informacji do procedury okna zapisane w `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage  
 Wywołuje się po otrzymaniu ostatniego komunikatu (zazwyczaj `WM_NCDESTROY`).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna zostaną zniszczone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja `OnFinalMessage` nie działa, ale można ją zastąpić tę funkcję, aby obsłużyć oczyszczania, zanim niszczenie okna. Jeśli chcesz automatycznie usunąć obiekt na zniszczenie okna, należy wywołać `delete this;` w tej funkcji.  
  
##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow  
 Podklasy okna identyfikowane przez `hWnd` i dołącza go do `CWindowImpl` obiektu.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna jest podklasą klasy.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** czy okno jest pomyślnie podklasą; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Używa teraz podklasą okna [CWindowImpl::WindowProc](#windowproc). Oryginalną procedurę okna jest zapisywany w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  Nie wywołuj `SubclassWindow` Jeśli już o nazwie [Utwórz](#create).  
  
##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow  
 Odłącza okno podklasą od `CWindowImpl` obiektu i przywraca oryginalną procedurę okna zapisane w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do wcześniej utworzono podklasę okna.  
  
##  <a name="windowproc"></a>  CWindowImpl::WindowProc  
 Ta funkcja statyczna wykonuje procedurę okna.  
  
```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna.  
  
 `uMsg`  
 [in] Komunikat wysyłany do okna.  
  
 `wParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik przetwarzania komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 `WindowProc` używa domyślnej mapy komunikatów (zadeklarowana z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) do kierowania wiadomości na odpowiednie programy obsługi. W razie potrzeby `WindowProc` wywołania [DefWindowProc](#defwindowproc) dla przetwarzania dodatkowych komunikatów. Jeśli komunikatu końcowego nie jest obsługiwana, `WindowProc` wykonuje następujące czynności:  
  
-   Wykonuje unsubclassing, jeśli unsubclassed okna.  
  
-   Czyści `m_hWnd`.  
  
-   Wywołania [OnFinalMessage](#onfinalmessage) przed okna.  
  
 Można zastąpić `WindowProc` na inny mechanizm obsługi wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
