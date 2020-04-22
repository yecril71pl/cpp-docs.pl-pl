---
title: CContainedWindowT, klasa
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747744"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT, klasa

Ta klasa implementuje okno zawarte w innym obiekcie.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*Baza danych TBase*<br/>
Klasa podstawowa nowej klasy. Domyślną klasą `CWindow`podstawową jest .

*TWinTraits ( TWinTraits )*<br/>
Klasa cech definiujących style okna. Wartość domyślna to `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) jest specjalizacją `CContainedWindowT`. Jeśli chcesz zmienić klasę podstawową lub `CContainedWindowT` cechy, użyj bezpośrednio.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor. Inicjuje elementy członkowskie danych, aby określić, która mapa wiadomości będzie przetwarzać komunikaty zawartego okna.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::Tworzenie](#create)|Tworzy okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Zapewnia domyślne przetwarzanie wiadomości.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Zwraca bieżącą wiadomość.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Rejestruje klasę okna okna zawartego okna.|
|[CContainedWindowT::PodklasaWindow](#subclasswindow)|Podklasy okna.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Zmiany, która mapa wiadomości jest używana do przetwarzania wiadomości zawartych w oknie.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Przywraca okno wcześniej podklasy.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statyczne) Przetwarza wiadomości wysyłane do okna zawierającego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Określa, która mapa wiadomości będzie przetwarzać komunikaty zawartego okna.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Określa nazwę istniejącej klasy okna, na której będzie oparta nowa klasa okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje oryginalną procedurę okna klasy okna.|
|[CContainedWindowT::m_pObject](#m_pobject)|Wskazuje obiekt zawierający.|

## <a name="remarks"></a>Uwagi

`CContainedWindowT`implementuje okno zawarte w innym obiekcie. `CContainedWindowT`'s window procedure używa mapy wiadomości w obiekcie zawierającym do kierowania wiadomości do odpowiednich programów obsługi. Podczas konstruowania `CContainedWindowT` obiektu, należy określić, które mapy wiadomości mają być używane.

`CContainedWindowT`umożliwia utworzenie nowego okna przez przeklasyfikowanie istniejącej klasy okna. Metoda `Create` najpierw rejestruje klasę okna, która jest oparta `CContainedWindowT::WindowProc`na istniejącej klasie, ale używa . `Create`następnie tworzy okno na podstawie tej nowej klasy okna. Każde wystąpienie `CContainedWindowT` może nadklasy innej klasy okna.

`CContainedWindowT`obsługuje również podklasy okna. Metoda `SubclassWindow` dołącza istniejące okno do `CContainedWindowT` obiektu i zmienia `CContainedWindowT::WindowProc`procedurę okna na . Każde wystąpienie `CContainedWindowT` może podklasy innego okna.

> [!NOTE]
> Dla danego `CContainedWindowT` obiektu wywołaj `Create` `SubclassWindow`albo lub . Nie należy wywoływać obie metody na tym samym obiekcie.

Korzystając z **opcji Dodaj formant na podstawie** opcji w Kreatorze projektu `CContainedWindowT` ATL, kreator automatycznie doda element członkowski danych do klasy implementującej formant. Poniższy przykład pokazuje, jak zawarte okno jest zadeklarowane:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Korzystanie z okien w programie ATL|[Klasy okien atl](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) i kolejne tematy w programie Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

Konstruktor inicjuje elementy członkowskie danych.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>
[w] Nazwa istniejącej klasy okna, na której będzie oparte okno zawarte.

*Pobject*<br/>
[w] Wskaźnik do obiektu zawierającego, który deklaruje mapę wiadomości. Klasa tego obiektu musi pochodzić z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[w] Identyfikuje mapę wiadomości, która będzie przetwarzać wiadomości zawarte okno. Wartość domyślna 0 określa domyślną mapę wiadomości zadeklarowaną [za pomocą BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby użyć alternatywnej mapy wiadomości zadeklarowanej z [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)przekaż `msgMapID`.

### <a name="remarks"></a>Uwagi

Aby utworzyć nowe okno za pomocą [funkcji Utwórz,](#create)należy przekazać nazwę istniejącej klasy okna dla parametru *lpszClassName.* Na przykład zobacz [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) omówienie.

Istnieją trzy konstruktory:

- Konstruktor z trzema argumentami jest zazwyczaj wywoływany.

- Konstruktor z dwoma argumentami używa `TBase::GetWndClassName`nazwy klasy z .

- Konstruktor bez argumentów jest używany, jeśli chcesz dostarczyć argumenty później. Podczas późniejszego wywołania `Create`należy podać nazwę klasy okna, obiekt mapy wiadomości i identyfikator mapy wiadomości.

Jeśli podklasa istniejącego okna za pośrednictwem [podklasyWindow](#subclasswindow), *lpszClassName* wartość nie będzie używany; w związku z tym można przekazać NULL dla tego parametru.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>CContainedWindowT::Tworzenie

Wywołuje [RegisterWndSuperclass,](#registerwndsuperclass) aby zarejestrować klasę okna, która jest oparta na istniejącej klasie, ale używa [CContainedWindowT::WindowProc](#windowproc).

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>
[w] Nazwa istniejącej klasy okna, na której będzie oparte okno zawarte.

*Pobject*<br/>
[w] Wskaźnik do obiektu zawierającego, który deklaruje mapę wiadomości. Klasa tego obiektu musi pochodzić z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[w] Identyfikuje mapę wiadomości, która będzie przetwarzać wiadomości zawarte okno. Wartość domyślna 0 określa domyślną mapę wiadomości zadeklarowaną [za pomocą BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby użyć alternatywnej mapy wiadomości zadeklarowanej z [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)przekaż `msgMapID`.

*hWndRodziciek*<br/>
[w] Dojście do okna nadrzędnego lub właściciela.

*Rect*<br/>
[w] Struktura [RECT](/windows/win32/api/windef/ns-windef-rect) określająca położenie okna. Mogą `RECT` być przekazywane przez wskaźnik lub przez odwołanie.

*szWindowName (Nazwa)*<br/>
[w] Określa nazwę okna. Wartością domyślną jest NULL.

*Dwstyle*<br/>
[w] Styl okna. Wartością domyślną jest WS_CHILD &#124; WS_VISIBLE. Aby uzyskać listę możliwych wartości, zobacz [Tworzenie systemu WindowsWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w zestawie Windows SDK.

*Dwexstyle*<br/>
[w] Rozszerzony styl okna. Wartość domyślna to 0, co oznacza brak stylu rozszerzonego. Aby uzyskać listę możliwych wartości, zobacz [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*MenuOrID*<br/>
[w] W przypadku okna podrzędnego identyfikator okna. W przypadku okna najwyższego poziomu, uchwyt menu dla okna. Wartość domyślna to **0U**.

*lpCreateParam*<br/>
[w] Wskaźnik do danych tworzenia okna. Pełny opis można znaleźć w opisie parametru końcowego [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do nowo utworzonego okna; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Istniejąca nazwa klasy okna jest zapisywana w [m_lpszClassName](#m_lpszclassname). `Create`następnie tworzy okno na podstawie tej nowej klasy. Nowo utworzone okno jest automatycznie dołączane do `CContainedWindowT` obiektu.

> [!NOTE]
> Nie należy `Create` wywoływać, jeśli masz już wywołanie [PodklasyWindow](#subclasswindow).

> [!NOTE]
> Jeśli 0 jest używana jako wartość dla *parametru MenuOrID,* musi być określona jako 0U (wartość domyślna), aby uniknąć błędu kompilatora.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc

Wywoływane przez [WindowProc](#windowproc) do przetwarzania wiadomości nie obsługiwane przez mapę wiadomości.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Zwraca bieżącą`m_pCurrentMsg`wiadomość ( ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wiadomość, pakowane `MSG` w strukturze.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Przechowuje identyfikator mapy wiadomości aktualnie używanej dla okna zamkniętego.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Uwagi

Ta mapa wiadomości musi być zadeklarowana w obiekcie zawierającym.

Domyślna mapa wiadomości, zadeklarowana za pomocą [BEGIN_MSG_MAP,](message-map-macros-atl.md#begin_msg_map)jest zawsze identyfikowana przez zero. Alternatywna mapa wiadomości, zadeklarowana za pomocą [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)jest identyfikowana przez `msgMapID`.

`m_dwMsgMapID`jest najpierw inicjowany przez konstruktora i można go zmienić, wywołując [SwitchMessageMap](#switchmessagemap). Na przykład zobacz [CContainedWindowT Overview](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Określa nazwę istniejącej klasy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia [okna, Tworzenie](#create) rejestruje nową klasę okna, która jest oparta na tej istniejącej klasy, ale używa [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName`jest inicjowany przez konstruktora. Na przykład zobacz [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) omówienie.

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Jeśli zawarte okno jest podklasy, `m_pfnSuperWindowProc` wskazuje oryginalną procedurę okna klasy okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

Jeśli zawarte okno jest superclassed, co oznacza, że jest oparty na `m_pfnSuperWindowProc` klasie okna, który modyfikuje istniejącą klasę, wskazuje na istniejącą procedurę okna klasy okna.

Metoda [DefWindowProc](#defwindowproc) wysyła informacje o wiadomości `m_pfnSuperWindowProc`do procedury okna zapisanej w pliku .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject

Wskazuje obiekt zawierający `CContainedWindowT` obiekt.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Uwagi

Ten kontener, którego klasa musi pochodzić od [CMessageMap,](../../atl/reference/cmessagemap-class.md)deklaruje mapę komunikatów używaną przez zawarte okno.

`m_pObject`jest inicjowany przez konstruktora. Na przykład zobacz [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) omówienie.

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Wywoływane przez [Utwórz,](#create) aby zarejestrować klasę okna okna zawartego okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, atom, który jednoznacznie identyfikuje klasę okna jest zarejestrowany; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta klasa okna jest oparta na istniejącej klasie, ale używa [CContainedWindowT::WindowProc](#windowproc). Istniejąca procedura nazwy i okna klasy okna są zapisywane odpowiednio w [m_lpszClassName](#m_lpszclassname) i [m_pfnSuperWindowProc.](#m_pfnsuperwindowproc)

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::PodklasaWindow

Podklasy okna identyfikowane przez *hWnd* `CContainedWindowT` i dołącza go do obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Dojście do okna jest podklasy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno jest pomyślnie podklasyfikowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno podklasyczne używa teraz [CContainedWindowT::WindowProc](#windowproc). Oryginalna procedura okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> Nie dzwonić, `SubclassWindow` jeśli masz już wywołanie [Create](#create).

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Zmiany, która mapa wiadomości będzie używana do przetwarzania wiadomości zawartych w oknie.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
[w] Identyfikator mapy wiadomości. Aby użyć domyślnej mapy wiadomości zadeklarowanej za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), przekaż zero. Aby użyć alternatywnej mapy wiadomości zadeklarowanej z [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)przekaż `msgMapID`.

### <a name="remarks"></a>Uwagi

Mapa komunikatów musi być zdefiniowana w obiekcie zawierającym.

Początkowo należy określić identyfikator mapy wiadomości w konstruktorze.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Odłącza okno podklasy `CContainedWindowT` od obiektu i przywraca oryginalną procedurę okna, zapisaną w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bEchętna*<br/>
[w] Ustaw wartość TRUE, aby wymusić przywrócenie oryginalnej procedury `CContainedWindowT` okna, nawet jeśli procedura okna dla tego obiektu nie jest aktualnie aktywna. Jeśli *bForce* jest ustawiona na FAŁSZ, a procedura okna dla tego `CContainedWindowT` obiektu nie jest aktualnie aktywna, oryginalna procedura okna nie zostanie przywrócona.

### <a name="return-value"></a>Wartość zwracana

Dojście do okna wcześniej podklasy. Jeśli *bForce* jest ustawiona na FAŁSZ, a procedura okna dla tego `CContainedWindowT` obiektu nie jest aktualnie aktywna, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko wtedy, gdy chcesz przywrócić oryginalną procedurę okna przed zniszczeniem okna. W przeciwnym razie [WindowProc](#windowproc) automatycznie to zrobi, gdy okno zostanie zniszczone.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc

Ta metoda statyczna implementuje procedurę okna.

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

`WindowProc`kieruje wiadomości do mapy wiadomości identyfikowanych przez [m_dwMsgMapID](#m_dwmsgmapid). Jeśli to `WindowProc` konieczne, wywołuje [DefWindowProc dla](#defwindowproc) przetwarzania dodatkowych wiadomości.

## <a name="see-also"></a>Zobacz też

[Klasa CWindow](../../atl/reference/cwindow-class.md)<br/>
[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Klasa CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
