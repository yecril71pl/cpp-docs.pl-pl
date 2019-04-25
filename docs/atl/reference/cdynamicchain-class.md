---
title: Klasa CDynamicChain
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4b68198c17d7bd030b88bc78ad4de1367c914703
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259004"
---
# <a name="cdynamicchain-class"></a>Klasa CDynamicChain

Ta klasa dostarcza metody obsługi dynamicznego łańcucha mapy komunikatów.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CDynamicChain
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor.|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Określa, że komunikat Windows do innego obiektu mapie komunikatów.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Usuwa wpis mapy wiadomości z kolekcji.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Dodaje wpis mapy wiadomości do kolekcji lub modyfikuje istniejący wpis.|

## <a name="remarks"></a>Uwagi

`CDynamicChain` Umożliwia zarządzanie kolekcją mapy komunikatów, umożliwiając komunikat Windows były kierowane w czasie wykonywania, do innego obiektu mapy komunikatów.

Aby dodać obsługę dynamicznej łańcuch mapy wiadomości, wykonaj następujące czynności:

- Pochodzi z klasy `CDynamicChain`. W mapie komunikatów, należy określić [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makra do tworzenia łańcucha mapy komunikatów domyślne innego obiektu.

- Pochodzi każdej klasy, aby utworzyć łańcuch z [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap` zezwala na obiekt uwidocznić jej mapy wiadomości do innych obiektów.

- Wywołaj `CDynamicChain::SetChainEntry` do identyfikowania, której obiekt i jaką komunikaty zmapowana do tworzenia łańcucha.

Na przykład załóżmy, że klasa jest zdefiniowana w następujący sposób:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Klient następnie wywołuje `CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

gdzie `chainedObj` jest obiektem, połączonych i jest wystąpieniem obiektu klasy pochodzącej od `CMessageMap`. Teraz Jeśli `myCtl` odbiera komunikat, który nie jest obsługiwany przez `OnPaint` lub `OnSetFocus`, procedurę okna kieruje wiadomości do `chainedObj`firmy domyślne mapy wiadomości.

Aby uzyskać więcej informacji na temat łańcuch mapy wiadomości zobacz [mapy komunikatów](../../atl/message-maps-atl.md) w artykule "Klas okien ATL."

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

Określa, że komunikat Windows mapy komunikatów innego obiektu.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[in] Unikatowy identyfikator skojarzony z połączonych obiekt i jego mapy komunikatów.

*hWnd*<br/>
[in] Dojście do okna odbierania komunikatów.

*uMsg*<br/>
[in] Komunikat wysyłany do okna.

*wParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lResult*<br/>
[out] Wynik przetwarzania wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli komunikat jest w pełni przetwarzany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj procedurę okna `CallChain`, należy określić [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makra w mapie wiadomości. Aby uzyskać przykład, zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) Przegląd.

`CallChain` wymaga poprzednie wywołanie [SetChainEntry](#setchainentry) skojarzyć *dwChainID* wartości z obiektu i jego mapie komunikatów.

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

Konstruktor.

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

Destruktor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

Usuwa określony komunikat mapy z kolekcji.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[in] Unikatowy identyfikator skojarzony z połączonych obiekt i jego mapy komunikatów. Pierwotnie zdefiniować tę wartość za pomocą wywołania [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli Mapa komunikat został pomyślnie usunięty z kolekcji. W przeciwnym razie wartość FALSE.

##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry

Dodaje określony komunikat mapy do kolekcji.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parametry

*dwChainID*<br/>
[in] Unikatowy identyfikator skojarzony z połączonych obiekt i jego mapy komunikatów.

*pObject*<br/>
[in] Wskaźnik do obiektu łańcuchowych, deklarowanie mapie komunikatów. Ten obiekt musi pochodzić od klasy [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Identyfikator mapy komunikatów w połączonych obiektów. Wartość domyślna to 0, który identyfikuje mapy komunikatów domyślne, które są zadeklarowane za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby określić mapy komunikatów alternatywne zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), przekazać `msgMapID`.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli Mapa komunikat został pomyślnie dodany do kolekcji. W przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *dwChainID* wartość już istnieje w kolekcji, jego skojarzonego obiektu i mapy komunikatów, które są zastępowane przez *obiekt* i *dwMsgMapID*, odpowiednio. W przeciwnym razie jest dodawany nowy wpis.

## <a name="see-also"></a>Zobacz także

[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
