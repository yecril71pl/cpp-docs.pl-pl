---
title: Klasa CMessageMap
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326724"
---
# <a name="cmessagemap-class"></a>Klasa CMessageMap

Ta klasa umożliwia mapy komunikatu obiektu, aby uzyskać dostęp przez inny obiekt.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMessageMap::PprotwowindowMessage](#processwindowmessage)|Uzyskuje dostęp do mapy `CMessageMap`wiadomości w klasie pochodnej.|

## <a name="remarks"></a>Uwagi

`CMessageMap`jest abstrakcyjną klasą podstawową, która umożliwia dostęp do map komunikatów obiektu przez inny obiekt. Aby obiekt może udostępnić swoje mapy wiadomości, jego `CMessageMap`klasa musi pochodzić od .

ATL służy `CMessageMap` do obsługi zawartych okien i dynamicznych tworzenia łańcucha map komunikatów. Na przykład każda klasa zawierająca [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiekt `CMessageMap`musi pochodzić od . Poniższy kod pochodzi z przykładu [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) Za pośrednictwem [CComControl](../../atl/reference/ccomcontrol-class.md) `CAtlEdit` klasa automatycznie `CMessageMap`wywodzi się z .

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Ponieważ zawarte okno, `m_EditCtrl`użyje mapy wiadomości w klasie `CAtlEdit` zawierającej, `CMessageMap`pochodzi od .

Aby uzyskać więcej informacji na temat map wiadomości, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md) w artykule "Klasy okien ATL".

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::PprotwowindowMessage

Uzyskuje dostęp do mapy wiadomości identyfikowane przez `CMessageMap` *dwMsgMapID* w klasie pochodnej.

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>Parametry

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

*dwMsgMapID*<br/>
[w] Identyfikator mapy wiadomości, która będzie przetwarzać wiadomość. Domyślna mapa wiadomości, zadeklarowana za pomocą [BEGIN_MSG_MAP,](message-map-macros-atl.md#begin_msg_map)jest identyfikowana przez 0. Alternatywna mapa wiadomości, zadeklarowana za pomocą [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)jest identyfikowana przez `msgMapID`.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wiadomość jest w pełni obsługiwana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywoływana przez procedurę okna [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiektu lub obiektu, który jest dynamicznie łańcuch do mapy wiadomości.

## <a name="see-also"></a>Zobacz też

[Klasa CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
