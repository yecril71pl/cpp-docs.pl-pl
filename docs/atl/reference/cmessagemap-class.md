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
ms.openlocfilehash: 617b7b4592c96625b44fbe5c2b93da971a423128
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258536"
---
# <a name="cmessagemap-class"></a>Klasa CMessageMap

Ta klasa umożliwia mapy wiadomości obiektu, aby mieć dostęp przez inny obiekt.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Uzyskuje dostęp do mapy komunikatów w `CMessageMap`-klasy pochodnej.|

## <a name="remarks"></a>Uwagi

`CMessageMap` jest abstrakcyjna klasa bazowa, umożliwiająca komunikat obiektu mapuje uzyskiwał dostęp do innego obiektu. Aby obiekt do udostępnienia jej mapy komunikatów, swojej klasie musi pochodzić od klasy `CMessageMap`.

Używa ATL `CMessageMap` znajdujących się w pomocy technicznej systemu windows i łańcuch mapy wiadomości dynamiczne. Na przykład wszystkie klasy zawierające [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiekt musi pochodzić od klasy `CMessageMap`. Poniższy kod jest pobierana z [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) próbki. Za pomocą [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` automatycznie pochodną klasy `CMessageMap`.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Ponieważ zawartego okna `m_EditCtrl`, będzie używać mapy komunikatów w klasie zawierającej `CAtlEdit` pochodzi od klasy `CMessageMap`.

Aby uzyskać więcej informacji na temat mapy komunikatów zobacz [mapy wiadomości](../../atl/message-maps-atl.md) w artykule "Klas okien ATL."

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

Uzyskuje dostęp do mapy komunikatów identyfikowane przez *dwMsgMapID* w `CMessageMap`-klasy pochodnej.

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

*dwMsgMapID*<br/>
[in] Identyfikator mapy komunikatów, która będzie przetwarzać komunikat. Mapy wiadomości domyślnej, zadeklarowany za pomocą [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), jest identyfikowany przez 0. Mapy wiadomości alternatywny zadeklarowane za pomocą [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), jest identyfikowany przez `msgMapID`.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli komunikat jest w pełni obsługiwany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywoływane przez procedurę okna z [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) obiektu lub obiektu, który jest dynamicznie powiązany z na mapie komunikatów.

## <a name="see-also"></a>Zobacz także

[Klasa CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
