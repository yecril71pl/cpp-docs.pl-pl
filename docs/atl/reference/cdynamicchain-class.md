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
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327031"
---
# <a name="cdynamicchain-class"></a>Klasa CDynamicChain

Ta klasa zawiera metody obsługi dynamicznego tworzenia łańcucha map komunikatów.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CDynamicChain
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Konstruktor.|
|[CDynamicChain::~CDynamicChain](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Kieruje wiadomość systemu Windows do mapy wiadomości innego obiektu.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Usuwa wpis mapy wiadomości z kolekcji.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Dodaje wpis mapy wiadomości do kolekcji lub modyfikuje istniejący wpis.|

## <a name="remarks"></a>Uwagi

`CDynamicChain`zarządza kolekcją map komunikatów, umożliwiając kierowanie wiadomości systemu Windows w czasie wykonywania do mapy wiadomości innego obiektu.

Aby dodać obsługę dynamicznego tworzenia łańcuchów map wiadomości, wykonaj następujące czynności:

- Wywodź `CDynamicChain`swoją klasę z . Na mapie wiadomości określ [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) makra do łańcucha do domyślnej mapy wiadomości innego obiektu.

- Wywodź każdą klasę, do której chcesz łańcuchować z [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`umożliwia obiektowi udostępnienie jego mapy wiadomości do innych obiektów.

- Wywołanie, `CDynamicChain::SetChainEntry` aby zidentyfikować obiekt i mapę wiadomości, do której chcesz łańcuch.

Załóżmy na przykład, że klasa jest zdefiniowana w następujący sposób:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Następnie klient `CMyWindow::SetChainEntry`wywołuje:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

gdzie `chainedObj` jest obiektem łańcuchowym i jest wystąpieniem `CMessageMap`klasy pochodnej . Teraz, `myCtl` jeśli otrzyma wiadomość, która `OnPaint` nie `OnSetFocus`jest obsługiwana przez lub `chainedObj`, procedura okna kieruje wiadomość do domyślnej mapy wiadomości.

Aby uzyskać więcej informacji na temat tworzenia łańcucha map wiadomości, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md) w artykule "Klasy okien ATL".

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain

Kieruje wiadomość systemu Windows do mapy wiadomości innego obiektu.

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

*dwChainID (psiątkowicy)*<br/>
[w] Unikatowy identyfikator skojarzony z obiektem łańcuchowym i jego mapą wiadomości.

*Hwnd*<br/>
[w] Dojście do okna odbierającego wiadomość.

*uMsg*<br/>
[w] Wiadomość wysłana do okna.

*Wparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*lWyskuj*<br/>
[na zewnątrz] Wynik przetwarzania wiadomości.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wiadomość jest w pełni przetworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby procedura okna była `CallChain`wywoływana, należy określić [makro CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) na mapie wiadomości. Na przykład zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) omówienie.

`CallChain`wymaga poprzedniego wywołania [SetChainEntry](#setchainentry) skojarzyć wartość *dwChainID* z obiektem i jego mapą wiadomości.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain

Konstruktor.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain::~CDynamicChain

Destruktor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry

Usuwa mapę określonego komunikatu z kolekcji.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parametry

*dwChainID (psiątkowicy)*<br/>
[w] Unikatowy identyfikator skojarzony z obiektem łańcuchowym i jego mapą wiadomości. Wartość ta została pierwotnie zdefiniowana za pomocą wywołania [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli mapa wiadomości zostanie pomyślnie usunięta z kolekcji. W przeciwnym razie FALSE.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain::SetChainEntry

Dodaje mapę określonej wiadomości do kolekcji.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parametry

*dwChainID (psiątkowicy)*<br/>
[w] Unikatowy identyfikator skojarzony z obiektem łańcuchowym i jego mapą wiadomości.

*Pobject*<br/>
[w] Wskaźnik do obiektu łańcuchowego deklarującego mapę wiadomości. Ten obiekt musi pochodzić z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[w] Identyfikator mapy wiadomości w obiekcie łańcuchowym. Wartość domyślna to 0, która identyfikuje domyślną mapę wiadomości zadeklarowaną za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Aby określić mapę wiadomości alternatywnej zadeklarowaną za pomocą `msgMapID` [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)przekaż .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli mapa wiadomości zostanie pomyślnie dodana do kolekcji. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *dwChainID* wartość już istnieje w kolekcji, jego skojarzony obiekt i mapa wiadomości są zastępowane przez *pObject* i *dwMsgMapID*, odpowiednio. W przeciwnym razie zostanie dodany nowy wpis.

## <a name="see-also"></a>Zobacz też

[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
