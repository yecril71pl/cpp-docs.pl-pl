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
ms.openlocfilehash: 56b503dfcfbe4fae215f61081446bd3a5070af3c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835535"
---
# <a name="cwindowimpl-class"></a>Klasa CWindowImpl

Zapewnia metody tworzenia lub podklasy okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nowa klasa, która pochodzi od `CWindowImpl` .

*TBase*<br/>
Klasa bazowa klasy. Domyślnie Klasa bazowa to [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
[Klasa cech](../../atl/understanding-window-traits.md) , która definiuje style dla okna. Wartość domyślna to `CControlWinTraits`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowImpl:: Create](#create)|Tworzy okno.|

### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT

|Nazwa|Opis|
|-|-|
|[DefWindowProc](#defwindowproc)|Zapewnia domyślne przetwarzanie komunikatów.|
|[GetCurrentMessage](#getcurrentmessage)|Zwraca bieżącą wiadomość.|
|[GetWindowProc](#getwindowproc)|Zwraca bieżącą procedurę okna.|
|[OnFinalMessage](#onfinalmessage)|Wywoływana po odebraniu ostatniego komunikatu (zwykle WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Podklasa okna.|
|[UnsubclassWindow](#unsubclasswindow)|Przywraca poprzednio podklasy okno.|

### <a name="static-methods"></a>Metody statyczne

|Nazwa|Opis|
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Zwraca statyczne wystąpienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), które zarządza informacjami o klasie okna.|
|[WindowProc](#windowproc)|Przetwarza komunikaty wysyłane do okna.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje pierwotną procedurę okna klasy okna.|

## <a name="remarks"></a>Uwagi

Można użyć `CWindowImpl` do utworzenia okna lub podklasy istniejącego okna. `CWindowImpl`procedura okna używa mapy komunikatów do kierowania komunikatów do odpowiednich programów obsługi.

`CWindowImpl::Create` tworzy okno na podstawie informacji o klasie okna, które są zarządzane przez [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` zawiera makro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , co oznacza, że `CWndClassInfo` rejestruje nową klasę okna. Jeśli chcesz utworzyć Superklasa istniejącej klasy okna, Utwórz klasę z `CWindowImpl` i dołącz [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro. W takim przypadku `CWndClassInfo` rejestruje klasę okna, która jest oparta na istniejącej klasie, ale używa `CWindowImpl::WindowProc` . Na przykład:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Ponieważ `CWndClassInfo` zarządza informacjami dla tylko jednej klasy okna, każde okno utworzone za pośrednictwem wystąpienia `CWindowImpl` jest oparte na tej samej klasie okna.

`CWindowImpl` obsługuje również podklasy okna. `SubclassWindow`Metoda dołącza istniejące okno do `CWindowImpl` obiektu i zmienia procedurę okna na `CWindowImpl::WindowProc` . Każde wystąpienie elementu `CWindowImpl` może być podklasą innego okna.

> [!NOTE]
> Dla dowolnego `CWindowImpl` obiektu, wywołaj jedną `Create` lub `SubclassWindow` . Nie wywołuj obu metod dla tego samego obiektu.

Oprócz programu `CWindowImpl` ATL oferuje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) do utworzenia okna zawartego w innym obiekcie.

Destruktor klasy podstawowej (~ `CWindowImplRoot` ) gwarantuje, że okno zostanie usunięte przed zniszczeniem obiektu.

`CWindowImpl` pochodzi od `CWindowImplBaseT` , który pochodzi od `CWindowImplRoot` , który pochodzi z `TBase` i [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie kontrolek|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Używanie systemu Windows w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="cwindowimplcreate"></a><a name="create"></a> CWindowImpl:: Create

Tworzy okno oparte na nowej klasie okna.

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
podczas Uchwyt do okna nadrzędnego lub właściciela.

*cinania*<br/>
podczas Struktura [prostokąta](/windows/win32/api/windef/ns-windef-rect) określająca położenie okna. `RECT`Może być przekazywanie przez wskaźnik lub przez odwołanie.

*szWindowName*<br/>
podczas Określa nazwę okna. Wartość domyślna to NULL.

*dwStyle*<br/>
podczas Styl okna. Ta wartość jest połączona ze stylem dostarczonym przez klasę cech dla okna. Wartość domyślna daje cechom pełną kontrolę nad stylem. Listę możliwych wartości można znaleźć w temacie [Wind Window](/windows/win32/api/winuser/nf-winuser-createwindoww) in the Windows SDK.

*dwExStyle*<br/>
podczas Styl okna rozszerzonego. Ta wartość jest połączona ze stylem dostarczonym przez klasę cech dla okna. Wartość domyślna daje cechom pełną kontrolę nad stylem. Aby uzyskać listę możliwych wartości, zobacz [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*MenuOrID*<br/>
podczas Dla okna podrzędnego identyfikator okna. Dla okna najwyższego poziomu, uchwyt menu dla okna. Wartość domyślna to **0u**.

*lpCreateParam*<br/>
podczas Wskaźnik do danych tworzenia okna. Pełny opis można znaleźć w opisie parametru końcowego [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do nowo utworzonego okna. W przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

`Create` najpierw rejestruje klasę okna, jeśli nie została jeszcze zarejestrowana. Nowo utworzone okno zostanie automatycznie dołączone do `CWindowImpl` obiektu.

> [!NOTE]
> Nie wywołuj `Create` , jeśli masz już nazwę [SubclassWindow](#subclasswindow).

Aby użyć klasy okna, która jest oparta na istniejącej klasie okna, należy utworzyć klasę z `CWindowImpl` i uwzględnić makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . Procedura okna istniejącej klasy okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Aby uzyskać więcej informacji, zobacz Omówienie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

> [!NOTE]
> Jeśli wartość jest równa 0, parametr *MenuOrID* musi być określony jako 0u (wartość domyślna), aby uniknąć błędu kompilatora.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a> CWindowImpl::D efWindowProc

Wywoływane przez [WindowProc](#windowproc) , aby przetwarzać komunikaty, które nie są obsługiwane przez mapę komunikatów.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
podczas Wiadomość wysłana do okna.

*wParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów.

### <a name="remarks"></a>Uwagi

Domyślnie program `DefWindowProc` wywołuje funkcję Win32 [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) , aby wysyłał informacje o komunikatach do procedury okna określonej w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

Funkcja bez parametrów automatycznie pobiera zbędne parametry z bieżącej wiadomości.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a> CWindowImpl::GetCurrentMessage

Zwraca bieżący komunikat spakowany w `MSG` strukturze.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący komunikat.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a> CWindowImpl::GetWindowProc

Zwraca `WindowProc` , bieżącą procedurę okna.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca procedura okna.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zastąpić procedurę okna własną.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a> CWindowImpl::GetWndClassInfo

Wywołuje się, by uzyskać [dostęp do informacji](#create) o klasie okna.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Wartość zwracana

Statyczne wystąpienie elementu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Uwagi

Domyślnie `CWindowImpl` uzyskuje tę metodę za pomocą makra [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , które określa nową klasę okna.

Aby utworzyć nadrzędną klasę okna, należy poprowadzić klasę z `CWindowImpl` i uwzględnić makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , które ma zostać przesłonięte `GetWndClassInfo` . Aby uzyskać więcej informacji, zobacz Omówienie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

Oprócz używania DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS makra można przesłonić `GetWndClassInfo` własnymi implementacjami.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a> CWindowImpl:: m_pfnSuperWindowProc

W zależności od okna wskazuje jedną z poniższych procedur okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

|Typ okna|Procedura okna|
|--------------------|----------------------|
|Okno oparte na nowej klasie okna, określone za pomocą makra [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) .|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) funkcja Win32.|
|Okno oparte na klasie okna, która modyfikuje istniejącą klasę, określoną za pomocą makra [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) .|Procedura okna istniejącej klasy okna.|
|Okno podklasy.|Oryginalna procedura okna podklasy okna.|

[CWindowImpl::D efwindowproc](#defwindowproc) wysyła informacje o komunikatach do procedury okna zapisanej w `m_pfnSuperWindowProc` .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a> CWindowImpl::OnFinalMessage

Wywoływana po odebraniu ostatniego komunikatu (zwykle WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do uszkodzonego okna.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `OnFinalMessage` nie robi nic, ale można zastąpić tę funkcję, aby obsłużyć czyszczenie przed zniszczeniem okna. Jeśli chcesz automatycznie usunąć obiekt podczas niszczenia okna, możesz wywołać polecenie **delete this;** w tej funkcji.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a> CWindowImpl::SubclassWindow

Podklasy okno identyfikowane przez *Właściwość HWND* i dołącza je do `CWindowImpl` obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do okna podklasy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało pomyślnie podklasy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W oknie podklasy są teraz stosowane [CWindowImpl:: WindowProc](#windowproc). Oryginalna procedura okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> Nie wywołuj `SubclassWindow` , jeśli już wywołano [Tworzenie](#create).

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a> CWindowImpl::UnsubclassWindow

Odłącza okno podklasy od `CWindowImpl` obiektu i przywraca pierwotną procedurę okna zapisanego w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do okna, które zostało wcześniej podklasy.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a> CWindowImpl::WindowProc

Ta funkcja statyczna implementuje procedurę okna.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Uchwyt do okna.

*uMsg*<br/>
podczas Wiadomość wysłana do okna.

*wParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wynik przetwarzania komunikatów.

### <a name="remarks"></a>Uwagi

`WindowProc` używa domyślnej mapy komunikatów (zadeklarowanej z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) do kierowania komunikatów do odpowiednich programów obsługi. W razie potrzeby program `WindowProc` wywołuje [DefWindowProc](#defwindowproc) do dodatkowego przetwarzania komunikatów. Jeśli komunikat końcowy nie jest obsługiwany, program `WindowProc` wykonuje następujące czynności:

- Wykonuje operację rozpodklas, jeśli okno zostało podklasy.

- Wyczyść `m_hWnd` .

- Wywołuje [OnFinalMessage](#onfinalmessage) przed zniszczeniem okna.

Można przesłonić, `WindowProc` Aby zapewnić inny mechanizm obsługi komunikatów.

## <a name="see-also"></a>Zobacz też

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
