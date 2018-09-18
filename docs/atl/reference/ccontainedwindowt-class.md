---
title: Klasa CContainedWindowT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c64db5a041845bbd068bab1a72ad461740170b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040482"
---
# <a name="ccontainedwindowt-class"></a>Klasa CContainedWindowT

Ta klasa implementuje okno znajdujących się w innym obiekcie.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*Tpodstawowe*<br/>
Klasa bazowa nowej klasie. Domyślna klasa bazowa jest `CWindow`.

*TWinTraits*<br/>
Klasa cech, który definiuje Style okna. Wartość domyślna to `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) jest specjalizacją `CContainedWindowT`. Jeśli chcesz zmienić cechy lub klasy bazowej, użyj `CContainedWindowT` bezpośrednio.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor. Inicjuje składowe danych, aby określić, w mapie komunikatów, w której będzie przetwarzać komunikatów okien zawartych.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Tworzy okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Udostępnia domyślne przetwarzanie komunikatów.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Zwraca bieżący komunikat.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Rejestruje klasę okna zawartego okna.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Podklasy okna.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Zmiany w mapie komunikatów, w której jest używana do przetwarzania komunikatów zawartego okna.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Przywraca wcześniej będące podklasami okna.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statyczny) Przetwarza komunikaty wysyłane do zawartego okna.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identyfikuje w mapie komunikatów, w której będzie przetwarzać komunikaty zawartego okna.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Określa nazwę istniejącej klasy okna, na którym będzie opierać się nową klasę okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Wskazuje klasę okna oryginalnego procedurę okna.|
|[CContainedWindowT::m_pObject](#m_pobject)|Wskazuje zawierającego go obiektu.|

## <a name="remarks"></a>Uwagi

`CContainedWindowT` implementuje okno znajdujących się w innym obiekcie. `CContainedWindowT`użytkownika używa procedury okna komunikatu mapy w zawierającego go obiektu do komunikatów bezpośrednich odpowiednie programy obsługi. Podczas tworzenia `CContainedWindowT` obiektu, należy określić mapy wiadomości, które powinny być używane.

`CContainedWindowT` Służy do tworzenia nowego okna przez superclassing istniejącej klasy okna. `Create` Metoda najpierw rejestruje klasę okna, która opiera się na istniejącej klasy, ale używa `CContainedWindowT::WindowProc`. `Create` następnie tworzy okno, w oparciu o tej nowej klasy okna. Każde wystąpienie `CContainedWindowT` można superklasie klasy innego okna.

`CContainedWindowT` obsługuje również podklasy okna. `SubclassWindow` Metoda dołącza do istniejącego okna `CContainedWindowT` obiektu i zmienia procedury okna `CContainedWindowT::WindowProc`. Każde wystąpienie `CContainedWindowT` można podklasy innego okna.

> [!NOTE]
>  Dla dowolnej podanej `CContainedWindowT` obiektu, albo użyć wywołania `Create` lub `SubclassWindow`. Nie należy wywołać obu metod na tym samym obiekcie.

Kiedy używać **Dodaj kontrolkę na podstawie** opcji Kreator projektu ATL, Kreator automatycznie doda `CContainedWindowT` element członkowski danych do klasy Implementowanie formantu. Poniższy przykład pokazuje, jak zawartego okna jest zadeklarowany jako:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[ALT — samouczek](../../atl/active-template-library-atl-tutorial.md)|
|Korzystanie z systemu windows w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](https://msdn.microsoft.com/library/windows/desktop/ms632595) i kolejnych tematów w zestawie Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT

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

*lpszClassName*<br/>
[in] Nazwa istniejącej klasy okna, na którym będzie zależeć zawartego okna.

*Obiekt*<br/>
[in] Wskaźnik do obiektu zawierającego, która deklaruje mapy komunikatów. Klasa ten obiekt musi pochodzić od klasy [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Identyfikuje mapy komunikatów, który będzie przetwarzał zawartego okna komunikatów. Wartość domyślna: 0, określa mapy komunikatów domyślne, które są zadeklarowane za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Można użyć mapy wiadomości alternatywny zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), przekazać `msgMapID`.

### <a name="remarks"></a>Uwagi

Jeśli chcesz utworzyć nowe okno za pośrednictwem [Utwórz](#create), musisz przekazać nazwę istniejącej klasy okna dla *lpszClassName* parametru. Aby uzyskać przykład, zobacz [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) Przegląd.

Istnieją trzy konstruktory:

- Konstruktor z trzech argumentów jest zwykle nazywany.

- Konstruktor z dwóch argumentów używa nazwy klasy z `TBase::GetWndClassName`.

- Konstruktor bez argumentów jest używana, jeśli chcesz podać argumenty później. Po wywołaniu później należy podać nazwę klasy okna, obiekt mapy wiadomości i identyfikator mapy wiadomości `Create`.

Jeśli podklasy istniejącego okna za pośrednictwem [SubclassWindow](#subclasswindow), *lpszClassName* nie zostanie użyta wartość; w związku z tym, można przekazać wartości NULL dla tego parametru.

##  <a name="create"></a>  CContainedWindowT::Create

Wywołania [RegisterWndSuperclass](#registerwndsuperclass) zarejestrować klasy okna, która opiera się na istniejącej klasy, ale używa [CContainedWindowT::WindowProc](#windowproc).

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
[in] Nazwa istniejącej klasy okna, na którym będzie zależeć zawartego okna.

*Obiekt*<br/>
[in] Wskaźnik do obiektu zawierającego, która deklaruje mapy komunikatów. Klasa ten obiekt musi pochodzić od klasy [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Identyfikuje mapy komunikatów, który będzie przetwarzał zawartego okna komunikatów. Wartość domyślna: 0, określa mapy komunikatów domyślne, które są zadeklarowane za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Można użyć mapy wiadomości alternatywny zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), przekazać `msgMapID`.

*hWndParent*<br/>
[in] Dojście do okna nadrzędnego lub właściciela.

*Rect*<br/>
[in] A [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) Struktura określająca położenie okna. `RECT` Mogą być przekazywane przez wskaźnik lub przez odwołanie.

*szWindowName*<br/>
[in] Określa nazwę okna. Wartością domyślną jest NULL.

*dwStyle*<br/>
[in] Styl okna. Wartość domyślna to WS_CHILD &#124; WS_VISIBLE. Aby uzyskać listę możliwych wartości, zobacz [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) w zestawie Windows SDK.

*dwExStyle*<br/>
[in] Styl okna rozszerzonej. Wartość domyślna to 0, co oznacza nie rozszerzonego stylu. Aby uzyskać listę możliwych wartości, zobacz [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*MenuOrID*<br/>
[in] Dla okna podrzędnego identyfikator okna. Aby uzyskać oknem najwyższego poziomu uchwyt menu dla okna. Wartość domyślna to **0U**.

*lpCreateParam*<br/>
[in] Wskaźnik do danych tworzenie okien. Aby uzyskać pełny opis, zobacz opis ostatni parametr do [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt do nowo utworzonego okna; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Nazwa istniejącej klasy okna jest zapisywany w [m_lpszClassName](#m_lpszclassname). `Create` następnie tworzy okno, w oparciu o tej nowej klasy. Nowo utworzony okna jest automatycznie dołączany do `CContainedWindowT` obiektu.

> [!NOTE]
>  Nie wywołuj `Create` już ona wywołana [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Jeśli 0 jest używany jako wartość *MenuOrID* parametru musi być określona jako 0U (wartość domyślna) w celu uniknięcia błędu kompilatora.

##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc

Wywoływane przez [WindowProc](#windowproc) przetwarzania komunikatów, które nie są obsługiwane przez mapie komunikatów.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

Domyślnie `DefWindowProc` wywołania [CallWindowProc](https://msdn.microsoft.com/library/windows/desktop/ms633571) Win32/funkcja do wysyłania informacji wiadomości do procedury okna, określony w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage

Zwraca bieżący komunikat (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący komunikat, spakowane w `MSG` struktury.

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

Przechowuje identyfikator aktualnie używany dla zawartego okna mapy wiadomości.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Uwagi

Ta mapa wiadomości musi być zadeklarowana w zawierającego go obiektu.

Mapy wiadomości domyślnej, zadeklarowany za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), zawsze jest identyfikowany przez zero. Mapy wiadomości alternatywny zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), jest identyfikowany przez `msgMapID`.

`m_dwMsgMapID` najpierw jest inicjowane przez konstruktora i można ją zmienić, wywołując [SwitchMessageMap](#switchmessagemap). Aby uzyskać przykład, zobacz [Przegląd CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

Określa nazwę istniejącej klasy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia okna [Utwórz](#create) rejestruje nową klasę okna, opiera się na tym istniejącej klasy, która używa [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName` jest inicjowane przez konstruktora. Aby uzyskać przykład, zobacz [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) Przegląd.

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

Jeśli podklasy zawartego okna `m_pfnSuperWindowProc` wskazuje na oryginalnym procedurę okna klasy okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Uwagi

W przypadku podklasy zawartego okna, czyli jest oparty na klasę okna, która modyfikuje istniejącej klasy, `m_pfnSuperWindowProc` wskazuje procedurę okna istniejącej klasy okna.

[DefWindowProc](#defwindowproc) metoda wysyła informacje o wiadomości do procedurę okna zapisane w `m_pfnSuperWindowProc`.

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

Wskazuje na obiekt zawierający `CContainedWindowT` obiektu.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Uwagi

Ten kontener, w których klasa musi pochodzić od klasy [CMessageMap](../../atl/reference/cmessagemap-class.md), deklaruje mapy komunikatów używane przez zawartego okna.

`m_pObject` jest inicjowane przez konstruktora. Aby uzyskać przykład, zobacz [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) Przegląd.

##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass

Wywoływane przez [Utwórz](#create) zarejestrować klasy okna zawartego okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, atom, który jednoznacznie identyfikuje klasę okna zarejestrowany; w przeciwnym razie, wartość zero.

### <a name="remarks"></a>Uwagi

Ta klasa okna opiera się na istniejącej klasy, ale używa [CContainedWindowT::WindowProc](#windowproc). Istniejące klasy okna nazwy i okno procedury są zapisywane w [m_lpszClassName](#m_lpszclassname) i [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), odpowiednio.

##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow

Podklasy okna identyfikowane przez *hWnd* i dołącza je do `CContainedWindowT` obiektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Uchwyt okna jest podklasą klasy.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie jest podklasą klasy okna; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Używa teraz będące podklasami okna [CContainedWindowT::WindowProc](#windowproc). Oryginalny procedurę okna jest zapisywany w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nie wywołuj `SubclassWindow` już ona wywołana [Utwórz](#create).

##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap

Zmiany w mapie komunikatów, w której będzie służyć do przetwarzania komunikatów zawartego okna.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
[in] Identyfikator mapy wiadomości. Aby użyć domyślnej mapy komunikatów zadeklarowane za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), Przekaż wartość zero. Można użyć mapy wiadomości alternatywny zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), przekazać `msgMapID`.

### <a name="remarks"></a>Uwagi

Mapy wiadomości musi być zdefiniowany w zawierającego go obiektu.

Identyfikator mapy wiadomości jest początkowo Podaj w konstruktorze.

##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow

Odłącza okno będące podklasami z `CContainedWindowT` obiektu i przywrócenie oryginalnego procedurę okna, zapisane w [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bForce*<br/>
[in] Ustaw na wartość true, wymuś oryginalnego procedurę okna do przywrócenia nawet wtedy, gdy procedura okna, w tym `CContainedWindowT` obiekt nie jest obecnie aktywny. Jeśli *bForce* jest ustawiona na FALSE i procedurę okna, w tym `CContainedWindowT` obiekt nie jest obecnie aktywny, oryginalnym procedurę okna nie zostanie przywrócony.

### <a name="return-value"></a>Wartość zwracana

Dojście do okna, wcześniej należy do podklasy. Jeśli *bForce* jest ustawiona na FALSE i procedurę okna, w tym `CContainedWindowT` obiekt nie jest obecnie aktywny, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Tej metody należy użyć tylko wtedy, gdy chcesz wykonać przywrócenie oryginalnego procedurę okna, zanim okno zostanie zniszczone. W przeciwnym razie [WindowProc](#windowproc) automatycznie będziesz to robić, kiedy niszczony jest okna.

##  <a name="windowproc"></a>  CContainedWindowT::WindowProc

Ta metoda statyczna implementuje procedurę okna.

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

`WindowProc` kieruje komunikaty do mapy wiadomości identyfikowane przez [m_dwMsgMapID](#m_dwmsgmapid). Jeśli to konieczne, `WindowProc` wywołania [DefWindowProc](#defwindowproc) do przetwarzania komunikatów dodatkowe.

## <a name="see-also"></a>Zobacz też

[Klasa CWindow](../../atl/reference/cwindow-class.md)<br/>
[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Klasa CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
