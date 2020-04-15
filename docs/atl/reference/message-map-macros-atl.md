---
title: Makra mapy wiadomości (ATL)
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326226"
---
# <a name="message-map-macros-atl"></a>Makra mapy wiadomości (ATL)

Te makra definiują mapy wiadomości i wpisy.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Oznacza początek alternatywnej mapy wiadomości.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Oznacza początek domyślnej mapy wiadomości.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Łańcuchy do alternatywnej mapy wiadomości w klasie podstawowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Łańcuchy do alternatywnej mapy wiadomości w element członkowski danych klasy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Łańcuchy do domyślnej mapy wiadomości w klasie podstawowej.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Łańcuchy do mapy wiadomości w innej klasie w czasie wykonywania.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Łańcuchy do domyślnej mapy wiadomości w element członkowski danych klasy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi na podstawie kodu powiadomienia.|
|[COMMAND_HANDLER](#command_handler)|Mapuje WM_COMMAND wiadomość do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora elementu menu, formantu lub akceleratora.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi, na podstawie identyfikatora elementu menu, formantu lub akceleratora.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje pustą mapę wiadomości.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Zapewnia domyślny program obsługi dla odzwierciedlenie wiadomości, które nie są obsługiwane w inny sposób.|
|[END_MSG_MAP](#end_msg_map)|Oznacza koniec mapy wiadomości.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Przekazuje wiadomości powiadomień do okna nadrzędnego.|
|[MESSAGE_HANDLER](#message_handler)|Mapuje komunikat systemu Windows do funkcji obsługi.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje ciągły zakres komunikatów systemu Windows do funkcji obsługi.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi na podstawie kodu powiadomienia.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje WM_NOTIFY wiadomość do funkcji obsługi, na podstawie kodu powiadomień i identyfikatora formantu.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi na podstawie identyfikatora formantu.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odzwierciedla wiadomości powiadomień z powrotem do okna, które je wysłał.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomienia.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora elementu menu, formantu lub akceleratora.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie identyfikatora elementu menu, formantu lub akceleratora.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora formantu.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi na podstawie identyfikatora formantu.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontrolnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

Oznacza początek alternatywnej mapy wiadomości.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
[w] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

ATL identyfikuje każdą mapę wiadomości za pomocą liczby. Domyślna mapa wiadomości (zadeklarowana za pomocą BEGIN_MSG_MAP makra) jest identyfikowana przez 0. Alternatywna mapa wiadomości jest identyfikowana przez *msgMapID*.

Mapy wiadomości są używane do przetwarzania wiadomości wysyłanych do okna. Na przykład [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) umożliwia określenie identyfikatora mapy wiadomości w obiekcie zawierającym. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) następnie używa tej mapy wiadomości, aby skierować komunikaty zawartego okna do odpowiedniej funkcji obsługi lub do innej mapy wiadomości. Aby uzyskać listę makr, które deklarują funkcje obsługi, zobacz [BEGIN_MSG_MAP](#begin_msg_map).

Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych.

Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Należy pamiętać, że zawsze jest dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano domyślną mapę wiadomości i jedną mapę wiadomości alternatywnych, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie przedstawiono dwie mapy wiadomości alternatywnych. Domyślna mapa wiadomości jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

Oznacza początek domyślnej mapy wiadomości.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
[w] Nazwa klasy zawierającej mapę wiadomości.

### <a name="remarks"></a>Uwagi

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) używa domyślnej mapy wiadomości do przetwarzania wiadomości wysyłanych do okna. Mapa wiadomości kieruje wiadomości do odpowiedniej funkcji obsługi lub do innej mapy wiadomości.

Następujące makra mapują komunikat do funkcji obsługi. Ta funkcja musi być *zdefiniowana*w klasie .

|Makro|Opis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mapuje komunikat systemu Windows do funkcji obsługi.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje ciągły zakres komunikatów systemu Windows do funkcji obsługi.|
|[COMMAND_HANDLER](#command_handler)|Mapuje WM_COMMAND wiadomość do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora elementu menu, formantu lub akceleratora.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi, na podstawie identyfikatora elementu menu, formantu lub akceleratora.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mapuje komunikat WM_COMMAND do funkcji obsługi na podstawie kodu powiadomienia.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje ciągły zakres WM_COMMAND wiadomości do funkcji obsługi, na podstawie identyfikatora elementu menu, formantu lub akceleratora.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje WM_NOTIFY wiadomość do funkcji obsługi, na podstawie kodu powiadomień i identyfikatora formantu.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi na podstawie identyfikatora formantu.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY do funkcji obsługi na podstawie kodu powiadomienia.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje ciągły zakres WM_NOTIFY wiadomości do funkcji obsługi, na podstawie identyfikatora formantu.|

Następujące makra kierują wiadomości do innej mapy wiadomości. Ten proces jest nazywany "łańcuchem".

|Makro|Opis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Łańcuchy do domyślnej mapy wiadomości w klasie podstawowej.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Łańcuchy do domyślnej mapy wiadomości w element członkowski danych klasy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Łańcuchy do alternatywnej mapy wiadomości w klasie podstawowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Łańcuchy do alternatywnej mapy wiadomości w element członkowski danych klasy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Łańcuchy do domyślnej mapy wiadomości w innej klasie w czasie wykonywania.|

Następujące makra kierują komunikaty "odbite" z okna nadrzędnego. Na przykład formant zwykle wysyła komunikaty powiadomień do okna nadrzędnego do przetwarzania, ale okno nadrzędne może odzwierciedlać komunikat z powrotem do formantu.

|Makro|Opis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora elementu menu, formantu lub akceleratora.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie identyfikatora elementu menu, formantu lub akceleratora.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomienia.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbity komunikat WM_COMMAND do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora formantu.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi na podstawie identyfikatora formantu.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontrolnych.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbity komunikat WM_NOTIFY do funkcji obsługi, na podstawie kodu powiadomień i ciągłego zakresu identyfikatorów kontroli.|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Gdy `CMyExtWindow` obiekt odbiera komunikat WM_PAINT, wiadomość jest kierowana do `CMyExtWindow::OnPaint` rzeczywistego przetwarzania. Jeśli `OnPaint` wskaże, że wiadomość wymaga dalszego przetwarzania, wiadomość zostanie `CMyBaseWindow`przekierowana do domyślnej mapy wiadomości w pliku .

Oprócz domyślnej mapy wiadomości można zdefiniować alternatywną mapę wiadomości z [ALT_MSG_MAP](#alt_msg_map). Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych. W poniższym przykładzie pokazano domyślną mapę wiadomości i jedną mapę wiadomości alternatywnych, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie przedstawiono dwie mapy wiadomości alternatywnych. Domyślna mapa wiadomości jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Należy pamiętać, że zawsze jest dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Definiuje wpis na mapie wiadomości.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*klasa pachna*<br/>
[w] Nazwa klasy podstawowej zawierającej mapę wiadomości.

*msgMapID*<br/>
[w] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT kieruje wiadomości do alternatywnej mapy wiadomości w klasie podstawowej. Ta alternatywna mapa wiadomości musi być zadeklarowana za pomocą [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Aby kierować wiadomości do domyślnej mapy wiadomości klasy podstawowej (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP. Na przykład zobacz [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Definiuje wpis na mapie wiadomości.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*TheChainMember*<br/>
[w] Nazwa elementu członkowskiego danych zawierającego mapę wiadomości.

*msgMapID*<br/>
[w] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT_MEMBER kieruje wiadomości do alternatywnej mapy wiadomości w element członkowi danych. Ta alternatywna mapa wiadomości musi być zadeklarowana za pomocą [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Aby kierować wiadomości do domyślnej mapy wiadomości elementu członkowskiego danych (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP_MEMBER. Na przykład zobacz [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

Definiuje wpis na mapie wiadomości.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*klasa pachna*<br/>
[w] Nazwa klasy podstawowej zawierającej mapę wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP kieruje wiadomości do domyślnej mapy wiadomości klasy podstawowej (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)). Aby kierować wiadomości do alternatywnej mapy wiadomości klasy podstawowej (zadeklarowanej za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

W tym przykładzie przedstawiono następujące elementy:

- Jeśli procedura okna `CMyClass`używa domyślnej mapy `OnPaint` wiadomości i nie obsługuje wiadomości, `CMyBaseClass`wiadomość jest kierowana do domyślnej mapy wiadomości do przetworzenia.

- Jeśli procedura okna używa pierwszej alternatywnej `CMyClass`mapy wiadomości w `CMyBaseClass`, wszystkie wiadomości są kierowane do domyślnej mapy wiadomości.

- Jeśli procedura okna `CMyClass`używa drugiej alternatywnej `OnChar` mapy wiadomości i nie obsługuje wiadomości, wiadomość jest `CMyBaseClass`kierowana do określonej alternatywnej mapy wiadomości w pliku . `CMyBaseClass`musi zadeklarować tę mapę wiadomości z ALT_MSG_MAP(1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Definiuje wpis na mapie wiadomości.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
[w] Unikatowy identyfikator mapy wiadomości obiektu.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_DYNAMIC kieruje wiadomości w czasie wykonywania do domyślnej mapy wiadomości w innym obiekcie. Obiekt i jego mapa wiadomości są skojarzone z *identyfikatorem dynaChainID,* który definiujesz za pomocą [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Musisz wyprowadzić klasę `CDynamicChain` z aby użyć CHAIN_MSG_MAP_DYNAMIC. Na przykład zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) omówienie.

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne mapy wiadomości alternatywnych za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Definiuje wpis na mapie wiadomości.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*TheChainMember*<br/>
[w] Nazwa elementu członkowskiego danych zawierającego mapę wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_MEMBER kieruje wiadomości do domyślnej mapy wiadomości członka danych (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)). Aby kierować wiadomości do alternatywnej mapy wiadomości elementu członkowskiego danych (zadeklarowanej za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości od BEGIN_MSG_MAP. Następnie można zadeklarować kolejne mapy wiadomości alternatywnych za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

W tym przykładzie przedstawiono następujące elementy:

- Jeśli procedura okna `CMyClass`używa domyślnej mapy `OnPaint` wiadomości i nie obsługuje wiadomości, `m_obj`wiadomość jest kierowana do domyślnej mapy wiadomości do przetworzenia.

- Jeśli procedura okna używa pierwszej alternatywnej `CMyClass`mapy wiadomości w `m_obj`, wszystkie wiadomości są kierowane do domyślnej mapy wiadomości.

- Jeśli procedura okna `CMyClass`używa 's drugiej `OnChar` alternatywnej mapy wiadomości i nie obsługuje wiadomości, wiadomość `m_obj`jest kierowana do określonej mapy wiadomości alternatywnej . Klasa `CMyContainedClass` musi zadeklarować tę mapę wiadomości z ALT_MSG_MAP(1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Podobnie [jak COMMAND_HANDLER](#command_handler), ale mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) na podstawie tylko kodu powiadomienia.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

Definiuje wpis na mapie wiadomości.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora.

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

COMMAND_HANDLER mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) do określonej funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora formantu. Przykład:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Każda funkcja określona w COMMAND_HANDLER makra musi być zdefiniowana w następujący sposób:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Mapa wiadomości `bHandled` ustawia wartość `CommandHandler` PRAWDA przed wywołaniem. Jeśli `CommandHandler` nie w pełni obsługiwać `bHandled` komunikat, należy ustawić na FALSE, aby wskazać, że wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy wiadomości za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz COMMAND_HANDLER można użyć [MESSAGE_HANDLER](#message_handler) do mapowania wiadomości WM_COMMAND bez względu na identyfikator lub kod. W takim `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` przypadku wszystkie WM_COMMAND wiadomości `OnHandlerFunction`będą kierowane do .

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

Podobnie [jak COMMAND_HANDLER](#command_handler), ale mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) na podstawie tylko identyfikatora elementu menu, formantu lub akceleratora.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora wysyłającego wiadomość.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Podobnie [jak COMMAND_RANGE_HANDLER](#command_range_handler), ale mapy [WM_COMMAND](/windows/win32/menurc/wm-command) wiadomości z określonym kodem powiadomień z zakresu formantów do jednej funkcji obsługi.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze elementu menu, formantu lub akceleratora wysyłającego wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Podobnie [jak COMMAND_HANDLER](#command_handler), ale mapy [WM_COMMAND](/windows/win32/menurc/wm-command) wiadomości z zakresu formantów do jednej funkcji obsługi.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze elementu menu, formantu lub akceleratora wysyłającego wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Deklaruje pustą mapę wiadomości.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

DECLARE_EMPTY_MSG_MAP jest makro wygody, który wywołuje [makra BEGIN_MSG_MAP](#begin_msg_map) i [END_MSG_MAP,](#end_msg_map) aby utworzyć pustą mapę wiadomości:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Zapewnia domyślny program obsługi dla okna podrzędnego (formantu), który będzie odbierał odbite wiadomości; program obsługi prawidłowo przekaże nieobsługiwałem wiadomości do `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

Oznacza koniec mapy wiadomości.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

Zawsze używaj [makra BEGIN_MSG_MAP,](#begin_msg_map) aby oznaczyć początek mapy wiadomości. Użyj [ALT_MSG_MAP,](#alt_msg_map) aby zadeklarować kolejne mapy wiadomości alternatywnych.

Należy pamiętać, że zawsze jest dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano domyślną mapę wiadomości i jedną mapę wiadomości alternatywnych, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie przedstawiono dwie mapy wiadomości alternatywnych. Domyślna mapa wiadomości jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Przekazuje wiadomości powiadomień do okna nadrzędnego.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część mapy wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

Definiuje wpis na mapie wiadomości.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*Msg*<br/>
[w] Komunikat systemu Windows.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

MESSAGE_HANDLER mapuje komunikat systemu Windows do określonej funkcji obsługi.

Każda funkcja określona w MESSAGE_HANDLER makra musi być zdefiniowana w następujący sposób:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Mapa wiadomości `bHandled` ustawia wartość `MessageHandler` PRAWDA przed wywołaniem. Jeśli `MessageHandler` nie w pełni obsługiwać `bHandled` komunikat, należy ustawić na FALSE, aby wskazać, że wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy wiadomości za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz MESSAGE_HANDLER można używać [COMMAND_HANDLER](#command_handler) i [NOTIFY_HANDLER](#notify_handler) do mapowania odpowiednio [WM_COMMAND](/windows/win32/menurc/wm-command) i [WM_NOTIFY](/windows/win32/controls/wm-notify) wiadomości.

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Podobnie [jak MESSAGE_HANDLER](#message_handler), ale mapuje zakres komunikatów systemu Windows do jednej funkcji obsługi.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgFirst (Powierze)*<br/>
[w] Oznacza początek ciągłego zakresu wiadomości.

*msgLast (msgLast)*<br/>
[w] Oznacza koniec ciągłego zakresu wiadomości.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Podobnie [jak NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) wiadomość na podstawie tylko kodu powiadomienia.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

Definiuje wpis na mapie wiadomości.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator formantu wysyłającego wiadomość.

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

NOTIFY_HANDLER mapuje komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) do określonej funkcji obsługi, na podstawie kodu powiadomienia i identyfikatora formantu.

Każda funkcja określona w NOTIFY_HANDLER makra musi być zdefiniowana w następujący sposób:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Mapa wiadomości `bHandled` ustawia wartość `NotifyHandler` PRAWDA przed wywołaniem. Jeśli `NotifyHandler` nie w pełni obsługiwać `bHandled` komunikat, należy ustawić na FALSE, aby wskazać, że wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
> Zawsze rozpoczynaj mapę wiadomości z [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy wiadomości za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy wiadomości. Każda mapa wiadomości musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz NOTIFY_HANDLER można użyć [MESSAGE_HANDLER](#message_handler) do mapowania wiadomości WM_NOTIFY bez względu na identyfikator lub kod. W takim `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` przypadku wszystkie WM_NOTIFY wiadomości będą `OnHandlerFunction`kierowane do .

Aby uzyskać więcej informacji na temat korzystania z map wiadomości w pliku ATL, zobacz [Mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Podobnie [jak NOTIFY_HANDLER](#notify_handler), ale mapuje komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) na podstawie tylko identyfikatora formantu.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator formantu wysyłającego wiadomość.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Podobnie [jak NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapy [WM_NOTIFY](/windows/win32/controls/wm-notify) wiadomości z określonym kodem powiadomień z zakresu formantów do jednej funkcji obsługi.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze formantu wysyłającego wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Podobnie [jak NOTIFY_HANDLER](#notify_handler), ale mapy [WM_NOTIFY](/windows/win32/controls/wm-notify) wiadomości z zakresu formantów do jednej funkcji obsługi.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze formantu wysyłającego wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Odzwierciedla wiadomości powiadomień z powrotem do okna podrzędnego (formantu), który je wysłał.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część mapy wiadomości okna nadrzędnego.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Podobnie [jak COMMAND_CODE_HANDLER](#command_code_handler), ale mapy polecenia odzwierciedlone z okna nadrzędnego.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Podobnie [jak COMMAND_HANDLER](#command_handler), ale mapy polecenia odzwierciedlone z okna nadrzędnego.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora.

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Podobnie [jak COMMAND_ID_HANDLER](#command_id_handler), ale mapy polecenia odzwierciedlone z okna nadrzędnego.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobnie [jak COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapy polecenia odzwierciedlone z okna nadrzędnego.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*Kod*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Podobnie [jak COMMAND_RANGE_HANDLER](#command_range_handler), ale mapy polecenia odzwierciedlone z okna nadrzędnego.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Podobnie [jak NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapy powiadomień odzwierciedlonych z okna nadrzędnego.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Podobnie [jak NOTIFY_HANDLER](#notify_handler), ale mapy powiadomień odzwierciedlonych z okna nadrzędnego.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora.

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Podobnie [jak NOTIFY_ID_HANDLER](#notify_id_handler), ale mapy powiadomień odzwierciedlonych z okna nadrzędnego.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikator elementu menu, formantu lub akceleratora.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Podobnie [jak NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapy powiadomień odzwierciedlonych z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*Cd*<br/>
[w] Kod powiadomienia.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Podobnie [jak NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapy powiadomień odzwierciedlonych z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[w] Oznacza początek ciągłego zakresu identyfikatorów kontrolnych.

*idLast*<br/>
[w] Oznacza koniec ciągłego zakresu identyfikatorów kontrolnych.

*func*<br/>
[w] Nazwa funkcji obsługi wiadomości.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
