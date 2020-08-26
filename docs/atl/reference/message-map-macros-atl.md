---
title: Makra mapy komunikatów (ATL)
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
ms.openlocfilehash: 9917f31dbb115552cf9dc9bde24f7b6921611750
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835301"
---
# <a name="message-map-macros-atl"></a>Makra mapy komunikatów (ATL)

Te makra definiują mapy komunikatów i wpisy.

|Nazwa|Opis|
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Oznacza początek alternatywnej mapy komunikatów.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Oznacza początek domyślnej mapy komunikatów.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Tworzy łańcuch do alternatywnej mapy komunikatów w klasie bazowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch do alternatywnej mapy komunikatów w składowej danych klasy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch do domyślnej mapy komunikatów w klasie bazowej.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch do mapy komunikatów w innej klasie w czasie wykonywania.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch do domyślnej mapy komunikatów w składowej danych klasy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[COMMAND_HANDLER](#command_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora elementu menu, kontrolki lub akceleratora.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie identyfikatora elementu menu, kontrolki lub akceleratora.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje pustą mapę komunikatów.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Zapewnia domyślną obsługę komunikatów odbitych, które nie są obsługiwane w przeciwnym razie.|
|[END_MSG_MAP](#end_msg_map)|Oznacza koniec mapy komunikatów.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Przekazuje komunikaty powiadomień do okna nadrzędnego.|
|[MESSAGE_HANDLER](#message_handler)|Mapuje komunikat systemu Windows na funkcję procedury obsługi.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje ciągły zakres komunikatów systemu Windows do funkcji obsługi.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora sterowania.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie identyfikatora sterowania.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odzwierciedla komunikaty powiadomień z powrotem do okna, które je wysłało.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora elementu menu, kontrolki lub akceleratora.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie identyfikatora elementu menu, kontrolki lub akceleratora.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora sterowania.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie identyfikatora sterowania.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a> ALT_MSG_MAP

Oznacza początek alternatywnej mapy komunikatów.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
podczas Identyfikator mapy komunikatów.

### <a name="remarks"></a>Uwagi

ATL identyfikuje każdą mapę wiadomości według liczby. Domyślna mapa komunikatów (zadeklarowana za pomocą makra BEGIN_MSG_MAP) jest identyfikowana przez 0. Alternatywna Mapa komunikatów jest identyfikowana przez *msgMapID*.

Mapy komunikatów są używane do przetwarzania komunikatów wysyłanych do okna. Na przykład [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) umożliwia określenie identyfikatora mapy komunikatów w zawierającym go obiekcie. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) następnie używa tej mapy komunikatów do kierowania komunikatów zawartego okna do odpowiedniej funkcji obsługi lub do innej mapy komunikatów. Aby zapoznać się z listą makr, które deklarują funkcje programu obsługi, zobacz [BEGIN_MSG_MAP](#begin_msg_map).

Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów.

Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Należy zauważyć, że zawsze istnieje tylko jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje domyślną mapę komunikatów i jedną alternatywną mapę komunikatów, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie pokazano dwa alternatywne mapy komunikatów. Domyślna mapa komunikatów jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a> BEGIN_MSG_MAP

Oznacza początek domyślnej mapy komunikatów.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
podczas Nazwa klasy zawierającej mapę komunikatów.

### <a name="remarks"></a>Uwagi

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) używa domyślnej mapy komunikatów do przetwarzania komunikatów wysyłanych do okna. Mapa wiadomości kieruje komunikaty do odpowiedniej funkcji obsługi lub do innej mapy komunikatów.

Następujące makra mapują komunikat na funkcję programu obsługi. Ta funkcja musi być zdefiniowana w *theClass*.

|Makro|Opis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mapuje komunikat systemu Windows na funkcję procedury obsługi.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje ciągły zakres komunikatów systemu Windows do funkcji obsługi.|
|[COMMAND_HANDLER](#command_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora elementu menu, kontrolki lub akceleratora.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie identyfikatora elementu menu, kontrolki lub akceleratora.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mapuje komunikat WM_COMMAND na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje ciągły zakres komunikatów WM_COMMAND do funkcji obsługi na podstawie identyfikatora elementu menu, kontrolki lub akceleratora.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora sterowania.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie identyfikatora sterowania.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje ciągły zakres komunikatów WM_NOTIFY do funkcji obsługi na podstawie identyfikatora sterowania.|

Następujące makra kierują komunikaty do innej mapy komunikatów. Ten proces jest nazywany "łańcuchem".

|Makro|Opis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch do domyślnej mapy komunikatów w klasie bazowej.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch do domyślnej mapy komunikatów w składowej danych klasy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Tworzy łańcuch do alternatywnej mapy komunikatów w klasie bazowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch do alternatywnej mapy komunikatów w składowej danych klasy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch do domyślnej mapy komunikatów w innej klasie w czasie wykonywania.|

Następujące makra kierują komunikaty "odbite" z okna nadrzędnego. Na przykład kontrolka zwykle wysyła komunikaty powiadomień do okna nadrzędnego do przetworzenia, ale okno nadrzędne może odzwierciedlać komunikat z powrotem do kontrolki.

|Makro|Opis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora elementu menu, kontrolki lub akceleratora.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie identyfikatora elementu menu, kontrolki lub akceleratora.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odbicie WM_COMMAND komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i identyfikatora sterowania.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie identyfikatora sterowania.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie ciągłego zakresu identyfikatorów formantu.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odbicie WM_NOTIFY komunikatu na funkcję programu obsługi na podstawie kodu powiadomienia i ciągłego zakresu identyfikatorów sterowania.|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Gdy `CMyExtWindow` obiekt otrzymuje komunikat WM_PAINT, komunikat jest kierowany do `CMyExtWindow::OnPaint` rzeczywistego przetwarzania. Jeśli `OnPaint` wskazuje, że komunikat wymaga dalszych operacji przetwarzania, komunikat zostanie następnie skierowany do domyślnej mapy komunikatów w `CMyBaseWindow` .

Oprócz domyślnej mapy komunikatów można zdefiniować alternatywną mapę komunikatów z [ALT_MSG_MAP](#alt_msg_map). Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów. Poniższy przykład pokazuje domyślną mapę komunikatów i jedną alternatywną mapę komunikatów, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie pokazano dwa alternatywne mapy komunikatów. Domyślna mapa komunikatów jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Należy zauważyć, że zawsze istnieje tylko jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a> CHAIN_MSG_MAP_ALT

Definiuje wpis w mapie wiadomości.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
podczas Nazwa klasy bazowej zawierającej mapę komunikatów.

*msgMapID*<br/>
podczas Identyfikator mapy komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT kieruje komunikaty do alternatywnej mapy komunikatów w klasie bazowej. Należy zadeklarować tę alternatywną mapę wiadomości z [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Aby skierować komunikaty do domyślnej mapy komunikatów klasy podstawowej (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP. Aby zapoznać się z przykładem, zobacz [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a> CHAIN_MSG_MAP_ALT_MEMBER

Definiuje wpis w mapie wiadomości.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
podczas Nazwa elementu członkowskiego danych zawierającego mapę komunikatów.

*msgMapID*<br/>
podczas Identyfikator mapy komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT_MEMBER kieruje komunikaty do alternatywnej mapy komunikatów w składowej danych. Należy zadeklarować tę alternatywną mapę wiadomości z [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Aby przekierować komunikaty do domyślnej mapy komunikatów elementu członkowskiego danych (zadeklarowanej za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP_MEMBER. Aby zapoznać się z przykładem, zobacz [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a> CHAIN_MSG_MAP

Definiuje wpis w mapie wiadomości.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
podczas Nazwa klasy bazowej zawierającej mapę komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP kieruje komunikaty do domyślnej mapy komunikatów klasy podstawowej (zadeklarowane za pomocą [BEGIN_MSG_MAP](#begin_msg_map)). Aby skierować komunikaty do alternatywnej mapy komunikatów klasy podstawowej (zadeklarowanej za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Ten przykład ilustruje następujące kwestie:

- Jeśli procedura okna używa `CMyClass` domyślnej mapy komunikatów i `OnPaint` nie obsługuje komunikatu, komunikat jest kierowany do `CMyBaseClass` domyślnej mapy komunikatów do przetwarzania.

- Jeśli w procedurze okna jest używana pierwsza alternatywna Mapa komunikatów w programie `CMyClass` , wszystkie komunikaty są kierowane do `CMyBaseClass` domyślnej mapy komunikatów.

- Jeśli procedura okna używa `CMyClass` drugiej alternatywnej mapy komunikatów i nie obsługuje `OnChar` komunikatu, komunikat jest kierowany do określonej alternatywnej mapy komunikatów w `CMyBaseClass` . `CMyBaseClass` musi być zadeklarowana dla tej mapy komunikatów z ALT_MSG_MAP (1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a> CHAIN_MSG_MAP_DYNAMIC

Definiuje wpis w mapie wiadomości.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
podczas Unikatowy identyfikator mapy komunikatów obiektu.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_DYNAMIC kieruje komunikaty w czasie wykonywania do domyślnej mapy komunikatów w innym obiekcie. Obiekt i jego mapa komunikatów są skojarzone z *dynaChainID*, które definiujesz za pomocą [CDynamicChain:: SetChainEntry](cdynamicchain-class.md#setchainentry). Należy utworzyć klasę z, `CDynamicChain` Aby użyć CHAIN_MSG_MAP_DYNAMIC. Aby zapoznać się z przykładem, zobacz Omówienie [CDynamicChain](../../atl/reference/cdynamicchain-class.md) .

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a> CHAIN_MSG_MAP_MEMBER

Definiuje wpis w mapie wiadomości.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
podczas Nazwa elementu członkowskiego danych zawierającego mapę komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_MEMBER kieruje komunikaty do domyślnej mapy komunikatów elementu członkowskiego danych (Deklaracja z [BEGIN_MSG_MAP](#begin_msg_map)). Aby skierować komunikaty do alternatywnej mapy komunikatów elementu członkowskiego danych (zadeklarowanej za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu BEGIN_MSG_MAP. Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Ten przykład ilustruje następujące kwestie:

- Jeśli procedura okna używa `CMyClass` domyślnej mapy komunikatów i `OnPaint` nie obsługuje komunikatu, komunikat jest kierowany do `m_obj` domyślnej mapy komunikatów do przetwarzania.

- Jeśli w procedurze okna jest używana pierwsza alternatywna Mapa komunikatów w programie `CMyClass` , wszystkie komunikaty są kierowane do `m_obj` domyślnej mapy komunikatów.

- Jeśli procedura okna używa `CMyClass` drugiej alternatywnej mapy komunikatów i nie obsługuje `OnChar` komunikatu, komunikat jest kierowany do określonej alternatywnej mapy komunikatów `m_obj` . Klasa `CMyContainedClass` musi być zadeklarowana dla tej mapy komunikatów z ALT_MSG_MAP (1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="command_code_handler"></a><a name="command_code_handler"></a> COMMAND_CODE_HANDLER

Podobnie jak w przypadku [COMMAND_HANDLER](#command_handler), ale mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) wyłącznie na podstawie kodu powiadomienia.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="command_handler"></a><a name="command_handler"></a> COMMAND_HANDLER

Definiuje wpis w mapie wiadomości.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora.

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

COMMAND_HANDLER mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) na określoną funkcję procedury obsługi na podstawie kodu powiadomienia i identyfikatora kontroli. Na przykład:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Każda funkcja określona w makrze COMMAND_HANDLER musi być zdefiniowana w następujący sposób:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Mapowanie komunikatów jest ustawione `bHandled` na wartość true przed `CommandHandler` wywołaniem. Jeśli `CommandHandler` komunikat nie jest w pełni obsługiwany, powinien mieć ustawioną `bHandled` wartość false, aby wskazać, że komunikat musi zostać przetworzony.

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz COMMAND_HANDLER można użyć [MESSAGE_HANDLER](#message_handler) do mapowania wiadomości WM_COMMAND bez względu na identyfikator lub kod. W takim przypadku program `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` przekieruje wszystkie WM_COMMAND komunikaty do programu `OnHandlerFunction` .

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="command_id_handler"></a><a name="command_id_handler"></a> COMMAND_ID_HANDLER

Podobnie jak w [COMMAND_HANDLER](#command_handler), ale mapuje komunikat [WM_COMMAND](/windows/win32/menurc/wm-command) na podstawie identyfikatora elementu menu, formantu lub akceleratora.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora wysyłającego komunikat.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a> COMMAND_RANGE_CODE_HANDLER

Podobnie jak w [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje komunikaty [WM_COMMAND](/windows/win32/menurc/wm-command) z określonym kodem powiadomienia z zakresu formantów do jednej funkcji obsługi.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorach elementu menu, kontrolce lub akceleratorze wysyłającym komunikat.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="command_range_handler"></a><a name="command_range_handler"></a> COMMAND_RANGE_HANDLER

Podobnie jak w [COMMAND_HANDLER](#command_handler), ale mapuje komunikaty [WM_COMMAND](/windows/win32/menurc/wm-command) z zakresu formantów do jednej funkcji obsługi.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorach elementu menu, kontrolce lub akceleratorze wysyłającym komunikat.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a> DECLARE_EMPTY_MSG_MAP

Deklaruje pustą mapę komunikatów.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

DECLARE_EMPTY_MSG_MAP to wygodne makro, które wywołuje makra [BEGIN_MSG_MAP](#begin_msg_map) i [END_MSG_MAP](#end_msg_map) do utworzenia pustej mapy komunikatów:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a> DEFAULT_REFLECTION_HANDLER

Udostępnia domyślną procedurę obsługi dla okna podrzędnego (kontrolka), która będzie odbierać wiadomości odbite; program obsługi będzie prawidłowo przekazywać nieobsłużone komunikaty do programu `DefWindowProc` .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="end_msg_map"></a><a name="end_msg_map"></a> END_MSG_MAP

Oznacza koniec mapy komunikatów.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

Zawsze używaj makra [BEGIN_MSG_MAP](#begin_msg_map) , aby oznaczyć początek mapy komunikatów. Użyj [ALT_MSG_MAP](#alt_msg_map) , aby zadeklarować kolejne alternatywne mapy komunikatów.

Należy zauważyć, że zawsze istnieje tylko jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje domyślną mapę komunikatów i jedną alternatywną mapę komunikatów, z których każda zawiera jedną funkcję obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W następnym przykładzie pokazano dwa alternatywne mapy komunikatów. Domyślna mapa komunikatów jest pusta.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="forward_notifications"></a><a name="forward_notifications"></a> FORWARD_NOTIFICATIONS

Przekazuje komunikaty powiadomień do okna nadrzędnego.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część mapy komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="message_handler"></a><a name="message_handler"></a> MESSAGE_HANDLER

Definiuje wpis w mapie wiadomości.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*msg*<br/>
podczas Komunikat systemu Windows.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

MESSAGE_HANDLER mapuje komunikat systemu Windows do określonej funkcji procedury obsługi.

Każda funkcja określona w makrze MESSAGE_HANDLER musi być zdefiniowana w następujący sposób:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Mapowanie komunikatów jest ustawione `bHandled` na wartość true przed `MessageHandler` wywołaniem. Jeśli `MessageHandler` komunikat nie jest w pełni obsługiwany, powinien mieć ustawioną `bHandled` wartość false, aby wskazać, że komunikat musi zostać przetworzony.

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz MESSAGE_HANDLER można użyć [COMMAND_HANDLER](#command_handler) i [NOTIFY_HANDLER](#notify_handler) do mapowania komunikatów [WM_COMMAND](/windows/win32/menurc/wm-command) i [WM_NOTIFY](/windows/win32/controls/wm-notify) .

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="message_range_handler"></a><a name="message_range_handler"></a> MESSAGE_RANGE_HANDLER

Podobnie jak w [MESSAGE_HANDLER](#message_handler), ale mapuje zakres komunikatów systemu Windows do jednej funkcji obsługi.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgFirst*<br/>
podczas Oznacza początek ciągłego zakresu komunikatów.

*msgLast*<br/>
podczas Oznacza koniec ciągłego zakresu komunikatów.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a> NOTIFY_CODE_HANDLER

Podobnie jak w przypadku [NOTIFY_HANDLER](#notify_handler), ale mapuje komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) wyłącznie na podstawie kodu powiadomienia.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="notify_handler"></a><a name="notify_handler"></a> NOTIFY_HANDLER

Definiuje wpis w mapie wiadomości.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator kontrolki wysyłającej wiadomość.

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

NOTIFY_HANDLER mapuje komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) na określoną funkcję procedury obsługi na podstawie kodu powiadomienia i identyfikatora kontroli.

Każda funkcja określona w makrze NOTIFY_HANDLER musi być zdefiniowana w następujący sposób:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Mapowanie komunikatów jest ustawione `bHandled` na wartość true przed `NotifyHandler` wywołaniem. Jeśli `NotifyHandler` komunikat nie jest w pełni obsługiwany, powinien mieć ustawioną `bHandled` wartość false, aby wskazać, że komunikat musi zostać przetworzony.

> [!NOTE]
> Zawsze rozpoczynaj Mapowanie komunikatów przy użyciu [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować kolejne alternatywne mapy komunikatów za pomocą [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) oznacza koniec mapy komunikatów. Każda mapa komunikatów musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz NOTIFY_HANDLER można użyć [MESSAGE_HANDLER](#message_handler) do mapowania wiadomości WM_NOTIFY bez względu na identyfikator lub kod. W takim przypadku program `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` przekieruje wszystkie WM_NOTIFY komunikaty do programu `OnHandlerFunction` .

Aby uzyskać więcej informacji o używaniu map komunikatów w ATL, zobacz [mapy komunikatów](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a> NOTIFY_ID_HANDLER

Podobnie jak w przypadku [NOTIFY_HANDLER](#notify_handler), ale mapuje komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) wyłącznie na podstawie identyfikatora sterowania.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator kontrolki wysyłającej wiadomość.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a> NOTIFY_RANGE_CODE_HANDLER

Podobnie jak w [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje komunikaty [WM_NOTIFY](/windows/win32/controls/wm-notify) z określonym kodem powiadomienia z zakresu formantów do jednej funkcji obsługi.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze kontrolki wysyłającej wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a> NOTIFY_RANGE_HANDLER

Podobnie jak w [NOTIFY_HANDLER](#notify_handler), ale mapuje komunikaty [WM_NOTIFY](/windows/win32/controls/wm-notify) z zakresu formantów do jednej funkcji obsługi.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikatorze kontrolki wysyłającej wiadomość.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a> REFLECT_NOTIFICATIONS

Odzwierciedla komunikaty powiadomień z powrotem do okna podrzędnego (kontrolki), które je wysłało.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część mapy komunikatów okna nadrzędnego.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a> REFLECTED_COMMAND_CODE_HANDLER

Podobnie jak [COMMAND_CODE_HANDLER](#command_code_handler), ale mapuje polecenia odzwierciedlone w oknie nadrzędnym.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a> REFLECTED_COMMAND_HANDLER

Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje polecenia odzwierciedlone w oknie nadrzędnym.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora.

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a> REFLECTED_COMMAND_ID_HANDLER

Podobnie jak [COMMAND_ID_HANDLER](#command_id_handler), ale mapuje polecenia odzwierciedlone w oknie nadrzędnym.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a> REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobnie jak [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapuje polecenia odzwierciedlone w oknie nadrzędnym.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*kodu*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a> REFLECTED_COMMAND_RANGE_HANDLER

Podobnie jak [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje polecenia odzwierciedlone w oknie nadrzędnym.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a> REFLECTED_NOTIFY_CODE_HANDLER

Przypomina [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapuje powiadomienia z okna nadrzędnego.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a> REFLECTED_NOTIFY_HANDLER

Przypomina [NOTIFY_HANDLER](#notify_handler), ale mapuje powiadomienia z okna nadrzędnego.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora.

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a> REFLECTED_NOTIFY_ID_HANDLER

Przypomina [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapuje powiadomienia z okna nadrzędnego.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikator elementu menu, kontrolki lub akceleratora.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a> REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Przypomina [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapuje powiadomienia z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*płyt*<br/>
podczas Kod powiadomienia.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a> REFLECTED_NOTIFY_RANGE_HANDLER

Przypomina [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje powiadomienia z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
podczas Oznacza początek ciągłego zakresu identyfikatorów kontrolek.

*idLast*<br/>
podczas Oznacza koniec ciągłego zakresu identyfikatorów kontrolek.

*func*<br/>
podczas Nazwa funkcji obsługi komunikatów.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
