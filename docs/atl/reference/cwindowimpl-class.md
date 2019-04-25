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
ms.openlocfilehash: f835f2869af20a1cb22595837c317eb165ef5fe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276890"
---
# <a name="cwindowimpl-class"></a>Klasa CWindowImpl

Zawiera metody służące do tworzenia lub Tworzenie podklasy okna.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nowa klasa jest pochodną `CWindowImpl`.

*Tpodstawowe*<br/>
Klasa bazowa, klasy. Domyślnie klasa bazowa jest [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
A [klasa cech](../../atl/understanding-window-traits.md) definiujący Style okna. Wartość domyślna to `CControlWinTraits`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowImpl::Create](#create)|Tworzy okno.|

### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Udostępnia domyślne przetwarzanie komunikatów.|
|[GetCurrentMessage](#getcurrentmessage)|Zwraca bieżący komunikat.|
|[GetWindowProc](#getwindowproc)|Zwraca bieżącą procedurę okna.|
|[OnFinalMessage](#onfinalmessage)|Metoda wywoływana po odebraniu komunikatu ostatniej (zazwyczaj WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Podklasy okna.|
|[UnsubclassWindow](#unsubclasswindow)|Przywraca wcześniej będące podklasami okna.|

### <a name="static-methods"></a>Metody statyczne

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Zwraca wystąpienie statyczne klasy [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), który zarządza informacjami klasy okna.|
|[WindowProc](#windowproc)|Przetwarza komunikaty wysyłane do okna.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje klasę okna oryginalnego procedurę okna.|

## <a name="remarks"></a>Uwagi

Możesz użyć `CWindowImpl` tworzenia okna lub podklasy istniejącego okna. `CWindowImpl` procedurę okna przy użyciu mapy komunikatów kieruje komunikaty do odpowiedniej procedury obsługi.

`CWindowImpl::Create` Tworzy okno, na podstawie informacji klasy okna, który jest zarządzany przez [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` zawiera [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra, która oznacza, że `CWndClassInfo` rejestruje nowe klasy okna. Chcąc superklasie istniejącej klasy okna, pochodzi z klasy `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra. W tym przypadku `CWndClassInfo` rejestruje klasę okna, która opiera się na istniejącej klasy, ale używa `CWindowImpl::WindowProc`. Na przykład:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Ponieważ `CWndClassInfo` zarządza informacjami dla tylko jedną klasę okna, każde okno utworzonymi za pomocą wystąpienia `CWindowImpl` opiera się na tej samej klasy okna.

`CWindowImpl` obsługuje również podklasy okna. `SubclassWindow` Metoda dołącza do istniejącego okna `CWindowImpl` obiektu i zmienia procedury okna `CWindowImpl::WindowProc`. Każde wystąpienie `CWindowImpl` można podklasy innego okna.

> [!NOTE]
>  Dla dowolnej podanej `CWindowImpl` obiektu, albo użyć wywołania `Create` lub `SubclassWindow`. Nie należy wywoływać obu metod na tym samym obiekcie.

Oprócz `CWindowImpl`, ATL dostarcza [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) można utworzyć okna, który jest zawarty w innym obiekcie.

Destruktor klasy podstawowej (~ `CWindowImplRoot`) gwarantuje, że okno jest zniknął, zanim obiekt zostanie zniszczony.

`CWindowImpl` pochodzi od klasy `CWindowImplBaseT`, które wywodzi się z `CWindowImplRoot`, która pochodzi od klasy `TBase` i [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[ALT — samouczek](../../atl/active-template-library-atl-tutorial.md)|
|Korzystanie z systemu windows w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
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

Tworzy okno, w oparciu o nowe klasy okna.

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

*hWndParent*<br/>
[in] Dojście do okna nadrzędnego lub właściciela.

*Rect*<br/>
[in] A [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) Struktura określająca położenie okna. `RECT` Mogą być przekazywane przez wskaźnik lub przez odwołanie.

*szWindowName*<br/>
[in] Określa nazwę okna. Wartością domyślną jest NULL.

*dwStyle*<br/>
[in] Styl okna. Ta wartość zostanie połączona z style zapewniany przez klasę cech okna. Wartość domyślna zapewnia cech klasy pełną kontrolę nad stylu. Aby uzyskać listę możliwych wartości, zobacz [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) w zestawie Windows SDK.

*dwExStyle*<br/>
[in] Styl okna rozszerzonej. Ta wartość zostanie połączona z style zapewniany przez klasę cech okna. Wartość domyślna zapewnia cech klasy pełną kontrolę nad stylu. Aby uzyskać listę możliwych wartości, zobacz [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*MenuOrID*<br/>
[in] Dla okna podrzędnego identyfikator okna. Aby uzyskać oknem najwyższego poziomu uchwyt menu dla okna. Wartość domyślna to **0U**.

*lpCreateParam*<br/>
[in] Wskaźnik do danych tworzenie okien. Aby uzyskać pełny opis, zobacz opis ostatni parametr do [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt do nowo utworzonego okna. W przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

`Create` najpierw rejestruje klasę okna, jeśli nie została jeszcze zarejestrowana. Nowo utworzony okna jest automatycznie dołączany do `CWindowImpl` obiektu.

> [!NOTE]
>  Nie wywołuj `Create` już ona wywołana [SubclassWindow](#subclasswindow).

Aby użyć klasy okna, w oparciu o istniejące klasy okna, pochodzi z klasy `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra. Istniejące klasy okna procedurę okna jest zapisywany w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Przegląd.

> [!NOTE]
>  Jeśli 0 jest używany jako wartość *MenuOrID* parametru musi być określona jako 0U (wartość domyślna) w celu uniknięcia błędu kompilatora.

##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc

Wywoływane przez [WindowProc](#windowproc) przetwarzania komunikatów, które nie są obsługiwane przez mapie komunikatów.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
[in] Komunikat wysyłany do okna.

*wParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości.

### <a name="remarks"></a>Uwagi

Domyślnie `DefWindowProc` wywołania [CallWindowProc](/windows/desktop/api/winuser/nf-winuser-callwindowproca) Win32/funkcja do wysyłania informacji wiadomości do procedury okna, określony w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

Funkcja bez parametrów automatycznie pobiera wymagane parametry z bieżącego komunikatu.

##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage

Zwraca bieżący komunikat, spakowane w `MSG` struktury.

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

Wywoływane przez [Utwórz](#create) uzyskiwać dostęp do informacji klasy okna.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Wartość zwracana

Statyczne wystąpienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Uwagi

Domyślnie `CWindowImpl` uzyskuje tej metody za pomocą [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra, która określa nowe klasy okna.

Aby superklasie istniejącej klasy okna pochodną klasy z `CWindowImpl` i obejmują [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra, aby zastąpić `GetWndClassInfo`. Aby uzyskać więcej informacji, zobacz [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Przegląd.

Oprócz za pomocą makra DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS, można zastąpić `GetWndClassInfo` z Twojej własnej implementacji.

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

W zależności od okna punkty do jednej z poniższych procedur okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

|Typ okna|Procedury okna|
|--------------------|----------------------|
|Okno oparte na nową klasę okna, określony przez [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra.|[DefWindowProc](/windows/desktop/api/winuser/nf-winuser-defwindowproca) funkcję Win32.|
|Okno w oparciu klasy okna, która modyfikuje istniejącej klasy, określony przez [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra.|Istniejące klasy okna procedurę okna.|
|Będące podklasami okno.|Okno będące podklasami oryginalnego procedurę okna.|

[CWindowImpl::DefWindowProc](#defwindowproc) wysyła komunikat informacje zapisane w procedurę okna `m_pfnSuperWindowProc`.

##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage

Wywołuje się po otrzymaniu ostatniego komunikatu (zazwyczaj WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Dojście do okna niszczone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja klasy `OnFinalMessage` nie robi nic, ale możesz zastąpić tę funkcję, aby obsłużyć czyszczenia, zanim niszczenie okna. Jeśli chcesz automatycznie usunąć obiektu na zniszczenie okna, można wywołać **usunąć ten;** w tej funkcji.

##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow

Podklasy okna identyfikowane przez *hWnd* i dołącza je do `CWindowImpl` obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Uchwyt okna jest podklasą klasy.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie jest podklasą klasy okna; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Używa teraz będące podklasami okna [CWindowImpl::WindowProc](#windowproc). Oryginalny procedurę okna jest zapisywany w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nie wywołuj `SubclassWindow` już ona wywołana [Utwórz](#create).

##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow

Odłącza okno będące podklasami z `CWindowImpl` obiektu i przywrócenie oryginalnego procedurę okna, zapisane w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do okna, wcześniej należy do podklasy.

##  <a name="windowproc"></a>  CWindowImpl::WindowProc

Ta funkcja statyczna implementuje procedurę okna.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Dojście do okna.

*uMsg*<br/>
[in] Komunikat wysyłany do okna.

*wParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania wiadomości.

### <a name="remarks"></a>Uwagi

`WindowProc` używa domyślnej mapy komunikatów (zadeklarowanych za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) do przekierowywania komunikatów do odpowiedniej procedury obsługi. Jeśli to konieczne, `WindowProc` wywołania [DefWindowProc](#defwindowproc) do przetwarzania komunikatów dodatkowe. Jeśli komunikat końcowy nie jest obsługiwany, `WindowProc` wykonuje następujące czynności:

- Wykonuje unsubclassing, jeśli unsubclassed okna.

- Czyści `m_hWnd`.

- Wywołania [OnFinalMessage](#onfinalmessage) przed okno zostanie zniszczone.

Można zastąpić `WindowProc` inny mechanizm obsługi wiadomości.

## <a name="see-also"></a>Zobacz także

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
