---
title: Klasa CContainedWindowT
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
ms.openlocfilehash: 2eae6e149cf6f7422d0653c1c15f46985d8d55c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496845"
---
# <a name="ccontainedwindowt-class"></a>Klasa CContainedWindowT

Ta klasa implementuje okno zawarte w innym obiekcie.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Klasa bazowa nowej klasy. Domyślną klasą bazową `CWindow`jest.

*TWinTraits*<br/>
Klasa cech, która definiuje style dla okna. Wartość domyślna to `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) to specjalizacja `CContainedWindowT`. Jeśli chcesz zmienić klasę bazową lub cechy, użyj `CContainedWindowT` bezpośrednio.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor. Inicjuje składowe danych, aby określić, która mapa komunikatów będzie przetwarzać komunikaty zawarte w oknie.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT:: Create](#create)|Tworzy okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Zapewnia domyślne przetwarzanie komunikatów.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Zwraca bieżącą wiadomość.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Rejestruje klasę okna zawartego okna.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Podklasa okna.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Zmienia, która mapa wiadomości jest używana do przetwarzania komunikatów zawartego okna.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Przywraca poprzednio podklasy okno.|
|[CContainedWindowT::WindowProc](#windowproc)|Ruchom Przetwarza komunikaty wysyłane do zawartego okna.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Określa, która mapa komunikatów będzie przetwarzać komunikaty zawarte w oknie.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Określa nazwę istniejącej klasy okna, na której będzie oparta Nowa Klasa okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje pierwotną procedurę okna klasy okna.|
|[CContainedWindowT::m_pObject](#m_pobject)|Wskazuje obiekt zawierający.|

## <a name="remarks"></a>Uwagi

`CContainedWindowT`implementuje okno zawarte w innym obiekcie. `CContainedWindowT`procedura okna programu używa mapy komunikatów w obiekcie zawierającym do kierowania komunikatów do odpowiednich programów obsługi. Podczas konstruowania `CContainedWindowT` obiektu należy określić, która mapa wiadomości powinna być używana.

`CContainedWindowT`umożliwia utworzenie nowego okna przez nadklasowe istniejące klasy okien. Metoda najpierw rejestruje klasę okna, która jest oparta na istniejącej klasie, ale używa `CContainedWindowT::WindowProc`. `Create` `Create`następnie tworzy okno w oparciu o tę nową klasę okna. Każde wystąpienie elementu `CContainedWindowT` może superklasy inną klasę okna.

`CContainedWindowT`obsługuje również podklasy okna. Metoda dołącza istniejące okno `CContainedWindowT` do obiektu i zmienia procedurę okna na `CContainedWindowT::WindowProc`. `SubclassWindow` Każde wystąpienie elementu `CContainedWindowT` może być podklasą innego okna.

> [!NOTE]
>  Dla dowolnego `CContainedWindowT` obiektu, wywołaj jedną `Create` lub `SubclassWindow`. Nie należy wywoływać obu metod dla tego samego obiektu.

W przypadku korzystania z opcji **Dodaj kontrolkę opartą na** użyciu w Kreatorze projektu ATL Kreator automatycznie doda `CContainedWindowT` element członkowski danych do klasy implementującej formant. Poniższy przykład pokazuje, jak jest zadeklarowane zawarte okno:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie kontrolek|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Używanie systemu Windows w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Okna](/windows/win32/winmsg/windows) i kolejne tematy w Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

Konstruktor inicjuje składowe danych.

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

*lpszClassName*<br/>
podczas Nazwa istniejącej klasy okna, na której będzie oparte zawarte okno.

*pObject*<br/>
podczas Wskaźnik do obiektu zawierającego, który deklaruje mapę komunikatów. Klasa tego obiektu musi pochodzić od [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
podczas Identyfikuje mapę wiadomości, która będzie przetwarzać komunikaty zawarte w oknie. Wartość domyślna (0) określa domyślną mapę komunikatów zadeklarowaną z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby użyć alternatywnej mapy komunikatów zadeklarowanej z [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`Przekaż.

### <a name="remarks"></a>Uwagi

Jeśli chcesz utworzyć nowe okno za pomocą [tworzenia](#create), musisz przekazać nazwę istniejącej klasy okna dla parametru *lpszClassName* . Aby zapoznać się z przykładem, zobacz Omówienie [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) .

Istnieją trzy konstruktory:

- Konstruktor z trzema argumentami jest zazwyczaj wywoływany.

- Konstruktor z dwoma argumentami używa nazwy klasy z `TBase::GetWndClassName`.

- Konstruktor bez argumentów jest używany, jeśli chcesz później podać argumenty. Podczas późniejszego wywołania `Create`należy podać nazwę klasy okna, obiekt mapy komunikatów i identyfikator mapy komunikatów.

Jeśli utworzysz podklasę istniejącego okna za pomocą [SubclassWindow](#subclasswindow), wartość *lpszClassName* nie zostanie użyta; w związku z tym, można przekazać wartość NULL dla tego parametru.

##  <a name="create"></a>CContainedWindowT:: Create

Wywołuje [RegisterWndSuperclass](#registerwndsuperclass) , aby zarejestrować klasę okna, która jest oparta na istniejącej klasie, ale używa [CContainedWindowT:: WindowProc](#windowproc).

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

*lpszClassName*<br/>
podczas Nazwa istniejącej klasy okna, na której będzie oparte zawarte okno.

*pObject*<br/>
podczas Wskaźnik do obiektu zawierającego, który deklaruje mapę komunikatów. Klasa tego obiektu musi pochodzić od [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
podczas Identyfikuje mapę wiadomości, która będzie przetwarzać komunikaty zawarte w oknie. Wartość domyślna (0) określa domyślną mapę komunikatów zadeklarowaną z [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby użyć alternatywnej mapy komunikatów zadeklarowanej z [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`Przekaż.

*hWndParent*<br/>
podczas Uchwyt do okna nadrzędnego lub właściciela.

*cinania*<br/>
podczas Struktura [prostokąta](/previous-versions/dd162897\(v=vs.85\)) określająca położenie okna. `RECT` Może być przekazywanie przez wskaźnik lub przez odwołanie.

*szWindowName*<br/>
podczas Określa nazwę okna. Wartość domyślna to NULL.

*dwStyle*<br/>
podczas Styl okna. Wartość domyślna to WS_CHILD &#124; WS_VISIBLE. Listę możliwych wartości można znaleźć w temacie [Wind Window](/windows/win32/api/winuser/nf-winuser-createwindoww) in the Windows SDK.

*dwExStyle*<br/>
podczas Styl okna rozszerzonego. Wartość domyślna to 0, co oznacza brak stylu rozszerzonego. Aby uzyskać listę możliwych wartości, zobacz [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*MenuOrID*<br/>
podczas Dla okna podrzędnego identyfikator okna. Dla okna najwyższego poziomu, uchwyt menu dla okna. Wartość domyślna to **0u**.

*lpCreateParam*<br/>
podczas Wskaźnik do danych tworzenia okna. Pełny opis można znaleźć w opisie parametru końcowego [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do nowo utworzonego okna; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Istniejąca nazwa klasy okna jest zapisywana w [m_lpszClassName](#m_lpszclassname). `Create`następnie tworzy okno na podstawie tej nowej klasy. Nowo utworzone okno zostanie automatycznie dołączone do `CContainedWindowT` obiektu.

> [!NOTE]
>  Nie wywołuj `Create` , jeśli masz już nazwę [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Jeśli wartość jest równa 0, parametr *MenuOrID* musi być określony jako 0u (wartość domyślna), aby uniknąć błędu kompilatora.

##  <a name="defwindowproc"></a>CContainedWindowT::D efWindowProc

Wywoływane przez [WindowProc](#windowproc) , aby przetwarzać komunikaty, które nie są obsługiwane przez mapę komunikatów.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

Domyślnie program wywołuje `DefWindowProc` funkcję Win32 [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) , aby wysyłał informacje o komunikatach do procedury okna określonej w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Zwraca bieżący komunikat (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący komunikat spakowany w `MSG` strukturze.

##  <a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Przechowuje identyfikator mapy komunikatów aktualnie używanej dla zawartego okna.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Uwagi

Ta mapa komunikatów musi być zadeklarowana w zawierającym go obiekcie.

Domyślna mapa komunikatów zadeklarowana za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)jest zawsze identyfikowana przez zero. Alternatywna Mapa komunikatów zadeklarowana z [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)jest identyfikowana przez `msgMapID`.

`m_dwMsgMapID`jest najpierw inicjowany przez konstruktora i można go zmienić przez wywołanie [SwitchMessageMap](#switchmessagemap). Aby zapoznać się z przykładem, zobacz [Omówienie CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

Określa nazwę istniejącej klasy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia okna, [Utwórz](#create) rejestruje nową klasę okna, która jest oparta na tej istniejącej klasie, ale używa [CContainedWindowT:: WindowProc](#windowproc).

`m_lpszClassName`jest inicjowany przez konstruktora. Aby zapoznać się z przykładem, zobacz Omówienie [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Jeśli zawarte okno jest podklasą, `m_pfnSuperWindowProc` wskazuje na pierwotną procedurę okna klasy Window.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

Jeśli zawarte okno jest superklasy, oznacza to, że jest oparta na klasie okna, która modyfikuje istniejącą klasę, `m_pfnSuperWindowProc` wskazuje na procedurę okna istniejącej klasy okna.

Metoda [DefWindowProc](#defwindowproc) wysyła informacje o komunikatach do procedury okna zapisanej `m_pfnSuperWindowProc`w.

##  <a name="m_pobject"></a>CContainedWindowT::m_pObject

Wskazuje obiekt zawierający `CContainedWindowT` obiekt.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Uwagi

Ten kontener, którego Klasa musi pochodzić od [CMessageMap](../../atl/reference/cmessagemap-class.md), deklaruje mapę wiadomości używaną przez zawarte okno.

`m_pObject`jest inicjowany przez konstruktora. Aby zapoznać się z przykładem, zobacz Omówienie [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Wywołane przez [utworzenie](#create) , aby zarejestrować klasę okna zawartego okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, Atom, który jednoznacznie identyfikuje zarejestrowanej klasy okna; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta klasa okna jest oparta na istniejącej klasie, ale używa [CContainedWindowT:: WindowProc](#windowproc). Istniejąca nazwa klasy okna i procedura okna są zapisywane odpowiednio w [m_lpszClassName](#m_lpszclassname) i [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

Podklasy okno identyfikowane przez *Właściwość HWND* i dołącza je do `CContainedWindowT` obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do okna podklasy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało pomyślnie podklasy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W oknie podklasy są teraz stosowane [CContainedWindowT:: WindowProc](#windowproc). Oryginalna procedura okna jest zapisywana w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nie wywołuj `SubclassWindow` , jeśli już wywołano [Tworzenie](#create).

##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Zmienia, która mapa wiadomości będzie używana do przetwarzania komunikatów zawartego okna.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
podczas Identyfikator mapy komunikatów. Aby użyć domyślnej mapy komunikatów zadeklarowanej za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), Przekaż zero. Aby użyć alternatywnej mapy komunikatów zadeklarowanej z [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`Przekaż.

### <a name="remarks"></a>Uwagi

Mapa wiadomości musi być zdefiniowana w zawierającym go obiekcie.

Początkowo należy określić identyfikator mapy komunikatów w konstruktorze.

##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Odłącza okno podklasy od `CContainedWindowT` obiektu i przywraca pierwotną procedurę okna zapisanego w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bForce*<br/>
podczas Ustaw wartość na true, aby wymusić przywrócenie oryginalnej procedury okna, nawet jeśli procedura okna dla `CContainedWindowT` tego obiektu nie jest obecnie aktywna. Jeśli *bForce* jest ustawiona na false, a procedura okna dla tego `CContainedWindowT` obiektu nie jest aktualnie aktywna, pierwotna procedura okna nie zostanie przywrócona.

### <a name="return-value"></a>Wartość zwracana

Dojście do okna, które zostało wcześniej podklasy. Jeśli *bForce* jest ustawiona na false, a procedura okna dla tego `CContainedWindowT` obiektu nie jest aktualnie aktywna, zwraca wartość null.

### <a name="remarks"></a>Uwagi

Tej metody należy użyć tylko wtedy, gdy chcesz przywrócić pierwotną procedurę okna, zanim okno zostanie zniszczone. W przeciwnym razie [WindowProc](#windowproc) automatycznie wykona to, gdy okno zostanie zniszczone.

##  <a name="windowproc"></a>CContainedWindowT::WindowProc

Ta metoda statyczna implementuje procedurę okna.

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

`WindowProc`kieruje komunikaty do mapy komunikatów identyfikowanej przez [m_dwMsgMapID](#m_dwmsgmapid). W razie potrzeby `WindowProc` program wywołuje [DefWindowProc](#defwindowproc) do dodatkowego przetwarzania komunikatów.

## <a name="see-also"></a>Zobacz także

[Klasa CWindow](../../atl/reference/cwindow-class.md)<br/>
[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Klasa CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
