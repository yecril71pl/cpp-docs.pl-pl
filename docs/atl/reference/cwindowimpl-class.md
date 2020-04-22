---
title: Klasa CWindowImpl
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: ea150195f06d12cd6549b9026714d9e1bbf392df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745998"
---
# <a name="cwindowimpl-class"></a>Klasa CWindowImpl

Udostępnia metody tworzenia lub podklasy okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja nowa klasa, `CWindowImpl`pochodząca od .

*Baza danych TBase*<br/>
Klasa podstawowa twojej klasy. Domyślnie klasą podstawową jest [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits ( TWinTraits )*<br/>
[Klasa cech definiujących](../../atl/understanding-window-traits.md) style okna. Wartość domyślna to `CControlWinTraits`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowImpl::Tworzenie](#create)|Tworzy okno.|

### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Zapewnia domyślne przetwarzanie wiadomości.|
|[GetCurrentMessage](#getcurrentmessage)|Zwraca bieżącą wiadomość.|
|[GetWindowProc (Proces GetWindowProc)](#getwindowproc)|Zwraca bieżącą procedurę okna.|
|[OnFinalMessage](#onfinalmessage)|Wywoływana po odebraniu ostatniej wiadomości (zazwyczaj WM_NCDESTROY).|
|[Subclasswindow](#subclasswindow)|Podklasy okna.|
|[UnsubclassWindow](#unsubclasswindow)|Przywraca okno wcześniej podklasy.|

### <a name="static-methods"></a>Metody statyczne

|||
|-|-|
|[GetWndClassInfo (GetWndClassInfo)](#getwndclassinfo)|Zwraca statyczne wystąpienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), które zarządza informacjami o klasie okna.|
|[Windowproc](#windowproc)|Przetwarza wiadomości wysyłane do okna.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[M_pfnsuperwindowproc](#m_pfnsuperwindowproc)|Wskazuje oryginalną procedurę okna klasy okna.|

## <a name="remarks"></a>Uwagi

Można użyć `CWindowImpl` do utworzenia okna lub podklasy istniejącego okna. procedura `CWindowImpl` okna używa mapy wiadomości do kierowania wiadomości do odpowiednich programów obsługi.

`CWindowImpl::Create`tworzy okno na podstawie informacji o klasie okna, które jest zarządzane przez [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`zawiera [makro DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) co oznacza, że `CWndClassInfo` rejestruje nową klasę okna. Jeśli chcesz nadklasywać istniejącej klasy okna, należy wyprowadzić klasę z `CWindowImpl` i dołączyć makro [DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) W takim `CWndClassInfo` przypadku rejestruje klasę okna, która jest oparta `CWindowImpl::WindowProc`na istniejącej klasie, ale używa . Przykład:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Ponieważ `CWndClassInfo` zarządza informacjami tylko dla jednej klasy okna, każde `CWindowImpl` okno utworzone za pośrednictwem wystąpienia jest oparte na tej samej klasie okna.

`CWindowImpl`obsługuje również podklasy okna. Metoda `SubclassWindow` dołącza istniejące okno do `CWindowImpl` obiektu i zmienia `CWindowImpl::WindowProc`procedurę okna na . Każde wystąpienie `CWindowImpl` może podklasy innego okna.

> [!NOTE]
> Dla danego `CWindowImpl` obiektu wywołaj `Create` `SubclassWindow`albo lub . Nie należy wywoływać obie metody na tym samym obiekcie.

Oprócz `CWindowImpl`, ATL zapewnia [CContainedWindow,](../../atl/reference/ccontainedwindowt-class.md) aby utworzyć okno, które znajduje się w innym obiekcie.

Destruktor klasy podstawowej `CWindowImplRoot`(~ ) zapewnia, że okno zniknie przed zniszczeniem obiektu.

`CWindowImpl`pochodzi z `CWindowImplBaseT`, który `CWindowImplRoot`pochodzi z , `TBase` który pochodzi z i [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Korzystanie z okien w programie ATL|[Klasy okien atl](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cmessagemap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Tworzenie

Tworzy okno na podstawie nowej klasy okna.

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

*hWndRodziciek*<br/>
[w] Dojście do okna nadrzędnego lub właściciela.

*Rect*<br/>
[w] Struktura [RECT](/windows/win32/api/windef/ns-windef-rect) określająca położenie okna. Mogą `RECT` być przekazywane przez wskaźnik lub przez odwołanie.

*szWindowName (Nazwa)*<br/>
[w] Określa nazwę okna. Wartością domyślną jest NULL.

*Dwstyle*<br/>
[w] Styl okna. Ta wartość jest połączona ze stylem zapewniana przez klasę cech dla okna. Wartość domyślna daje klasę cech pełną kontrolę nad stylem. Aby uzyskać listę możliwych wartości, zobacz [Tworzenie systemu WindowsWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w zestawie Windows SDK.

*Dwexstyle*<br/>
[w] Rozszerzony styl okna. Ta wartość jest połączona ze stylem zapewniana przez klasę cech dla okna. Wartość domyślna daje klasę cech pełną kontrolę nad stylem. Aby uzyskać listę możliwych wartości, zobacz [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*MenuOrID*<br/>
[w] W przypadku okna podrzędnego identyfikator okna. W przypadku okna najwyższego poziomu, uchwyt menu dla okna. Wartość domyślna to **0U**.

*lpCreateParam*<br/>
[w] Wskaźnik do danych tworzenia okna. Pełny opis można znaleźć w opisie parametru końcowego [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do nowo utworzonego okna. W przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

`Create`najpierw rejestruje klasę okna, jeśli nie została jeszcze zarejestrowana. Nowo utworzone okno jest automatycznie dołączane do `CWindowImpl` obiektu.

> [!NOTE]
> Nie należy `Create` wywoływać, jeśli masz już wywołanie [PodklasyWindow](#subclasswindow).

Aby użyć klasy okna, która jest oparta na istniejącej klasy okna, należy wyprowadzić klasę z `CWindowImpl` i dołączyć makro [DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) Procedura okna istniejącej klasy okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) omówienie.

> [!NOTE]
> Jeśli 0 jest używana jako wartość dla *parametru MenuOrID,* musi być określona jako 0U (wartość domyślna), aby uniknąć błędu kompilatora.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

Wywoływane przez [WindowProc](#windowproc) do przetwarzania wiadomości nie obsługiwane przez mapę wiadomości.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
[w] Wiadomość wysłana do okna.

*Wparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości.

### <a name="remarks"></a>Uwagi

Domyślnie `DefWindowProc` wywołuje wywołanie funkcji [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 w celu wysłania informacji o wiadomości do procedury okna określonej w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

Funkcja bez parametrów automatycznie pobiera potrzebne parametry z bieżącej wiadomości.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Zwraca bieżącą wiadomość, spakowane w `MSG` strukturze.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wiadomość.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Zwraca `WindowProc`, bieżącą procedurę okna.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca procedura okna.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zastąpić procedurę okna własną.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Wywoływane przez [Utwórz,](#create) aby uzyskać dostęp do informacji o klasie okna.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Wartość zwracana

Statyczne wystąpienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Uwagi

Domyślnie `CWindowImpl` uzyskuje tę metodę za pośrednictwem [makra DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) który określa nową klasę okna.

Aby naklasować istniejącą klasę okna, należy wyprowadzić klasę z `CWindowImpl` makra [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) i dołączyć do niego, aby zastąpić `GetWndClassInfo`jego makro. Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) omówienie.

Oprócz używania makr DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS można zastąpić `GetWndClassInfo` własną implementacją.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

W zależności od okna wskazuje jedną z następujących procedur okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

|Typ okna|Procedura okna|
|--------------------|----------------------|
|Okno oparte na nowej klasie okna, określone za pośrednictwem [makra DECLARE_WND_CLASS.](window-class-macros.md#declare_wnd_class)|Funkcja [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32.|
|Okno oparte na klasie okna, która modyfikuje istniejącą klasę, określoną za pośrednictwem [makra DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass)|Procedura okna istniejącej klasy okna.|
|Okno podklasy.|Procedura oryginalnego okna okna podklasy.|

[CWindowImpl::DefWindowProc](#defwindowproc) wysyła informacje o wiadomości do `m_pfnSuperWindowProc`procedury okna zapisanej w pliku .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Wywoływana po otrzymaniu ostatniej wiadomości (zazwyczaj WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna jest niszczony.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `OnFinalMessage` nic nie robi, ale można zastąpić tę funkcję do obsługi oczyszczania przed zniszczeniem okna. Jeśli chcesz automatycznie usunąć obiekt po zniszczeniu okna, możesz wywołać **usuń to;** w tej funkcji.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::PodklasaWindow

Podklasy okna identyfikowane przez *hWnd* `CWindowImpl` i dołącza go do obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Dojście do okna jest podklasy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno jest pomyślnie podklasyfikowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno podklasyczne używa teraz [CWindowImpl::WindowProc](#windowproc). Oryginalna procedura okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> Nie dzwonić, `SubclassWindow` jeśli masz już wywołanie [Create](#create).

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Odłącza okno podklasy `CWindowImpl` od obiektu i przywraca oryginalną procedurę okna, zapisaną w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do okna wcześniej podklasy.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc

Ta funkcja statyczna implementuje procedurę okna.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna.

*uMsg*<br/>
[w] Wiadomość wysłana do okna.

*Wparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości.

### <a name="remarks"></a>Uwagi

`WindowProc`używa domyślnej mapy wiadomości (zadeklarowanej za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) do kierowania wiadomości do odpowiednich programów obsługi. Jeśli to `WindowProc` konieczne, wywołuje [DefWindowProc dla](#defwindowproc) przetwarzania dodatkowych wiadomości. Jeśli komunikat końcowy nie jest `WindowProc` obsługiwany, wykonuje następujące czynności:

- Wykonuje anulowanie klasyfikacji, jeśli okno zostało anulowane.

- Czyści `m_hWnd`.

- Wywołuje [OnFinalMessage](#onfinalmessage) przed zniszczeniem okna.

Można `WindowProc` zastąpić, aby zapewnić inny mechanizm obsługi komunikatów.

## <a name="see-also"></a>Zobacz też

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
