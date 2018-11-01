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
ms.openlocfilehash: 5502dae40392679f47b691a822260accbf597dc0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555106"
---
# <a name="message-map-macros-atl"></a>Makra mapy komunikatów (ATL)

Te makra definiują mapy komunikatów i wpisów.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Oznacza początek mapy komunikatów alternatywne.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Oznacza początek domyślne mapy komunikatów.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Łańcuchy do mapowania alternatywnych wiadomości w klasie bazowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch mapy wiadomości alternatywny w element członkowski danych klasy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch mapy komunikatów domyślnego w klasie bazowej.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch mapy komunikatów w innej klasy w czasie wykonywania.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch mapy komunikatów domyślne w składowej danych klasy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie kodu powiadomień.|
|[COMMAND_HANDLER](#command_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i identyfikator elementu menu, formant lub klawiszy skrótów.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie identyfikatora elementu menu, formant lub klawiszy skrótów.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje mapę pustego komunikatu.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Udostępnia domyślny program obsługi komunikaty odbite, które nie są obsługiwane w inny sposób.|
|[END_MSG_MAP](#end_msg_map)|Oznacza koniec mapy komunikatów.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Przekazuje komunikaty powiadomień do okna nadrzędnego.|
|[MESSAGE_HANDLER](#message_handler)|Mapuje funkcji obsługi komunikatów Windows.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje funkcji obsługi komunikatów ciągły zakres Windows.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomień.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie identyfikatora kontroli.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odzwierciedla powiadomienia do okna, która wysłała je.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomień.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i identyfikator elementu menu, formant lub klawiszy skrótów.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie identyfikatora elementu menu, formant lub klawiszy skrótów.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomień.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie identyfikatora kontroli.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

Oznacza początek mapy komunikatów alternatywne.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
[in] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

ATL identyfikuje każdy mapy komunikatów przez liczbę. Mapy komunikatów domyślne (zadeklarowana za pomocą makra BEGIN_MSG_MAP) jest identyfikowany przez 0. Mapy komunikatów alternatywne jest identyfikowane za pomocą *msgMapID*.

Mapy komunikatów będą używani do przetwarzania komunikatów wysłanych do okna. Na przykład [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pozwala określić identyfikator mapy komunikatów w zawierającego go obiektu. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) następnie używa tej mapy wiadomości do przekierowywania zawartego okna komunikatów do funkcji odpowiedni program obsługi lub innej mapy wiadomości. Aby uzyskać listę makra, które deklarują funkcje programu obsługi, zobacz [BEGIN_MSG_MAP](#begin_msg_map).

Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne.

[END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Należy pamiętać, że jest zawsze dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

Poniższy kod przedstawia domyślny mapy komunikatów i jeden komunikat alternatywne mapy, każdy z nich zawierający jedną funkcję programu obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywne. Mapy komunikatów domyślne jest puste.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

Oznacza początek domyślne mapy komunikatów.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Nazwa klasy zawierającej mapie komunikatów.

### <a name="remarks"></a>Uwagi

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) przetwarza mapę komunikatów w domyślnej procesu komunikaty wysyłane do okna. Mapy komunikatów kieruje komunikaty do funkcji odpowiedni program obsługi lub innej mapy wiadomości.

Następujące makra mapowania wiadomości do funkcji programu obsługi. Ta funkcja musi być zdefiniowany w *theClass*.

|Macro|Opis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mapuje funkcji obsługi komunikatów Windows.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje funkcji obsługi komunikatów ciągły zakres Windows.|
|[COMMAND_HANDLER](#command_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i identyfikator elementu menu, formant lub klawiszy skrótów.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie identyfikatora elementu menu, formant lub klawiszy skrótów.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mapuje komunikatów WM_COMMAND funkcji obsługi, na podstawie kodu powiadomień.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje ciągły zakres wm_command — komunikaty do obsługi funkcji, na podstawie identyfikatora elementu menu, formant lub klawiszy skrótów.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie identyfikatora kontroli.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje komunikat WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomień.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapy wiadomości ciągły zakres WM_NOTIFY do obsługi funkcji, na podstawie identyfikatora kontroli.|

Następujące makra przekierowywania komunikatów do innej mapy wiadomości. Ten proces jest nazywany "łańcucha".

|Macro|Opis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Tworzy łańcuch mapy komunikatów domyślnego w klasie bazowej.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Tworzy łańcuch mapy komunikatów domyślne w składowej danych klasy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Łańcuchy do mapowania alternatywnych wiadomości w klasie bazowej.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Tworzy łańcuch mapy wiadomości alternatywny w element członkowski danych klasy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Tworzy łańcuch mapy komunikatów domyślne w innej klasy w czasie wykonywania.|

Następujące makra bezpośrednie "widoczne" wiadomości z okna nadrzędnego. Na przykład kontrolki zwykle wysyła powiadomienia do okna nadrzędnego dla przetwarzania, ale okno nadrzędne może odzwierciedlać komunikatu do kontrolki.

|Macro|Opis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i identyfikator elementu menu, formant lub klawiszy skrótów.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie identyfikatora elementu menu, formant lub klawiszy skrótów.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomień.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje komunikatów odbitych WM_COMMAND funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie identyfikatora kontroli.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomień.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie ciągłego zakresu identyfikatorów kontroli.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje komunikatów odbitych WM_NOTIFY funkcji obsługi, na podstawie kodu powiadomienia i ciągły zakres identyfikatorów kontroli.|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Gdy `CMyExtWindow` obiektu odbiera komunikat WM_PAINT, komunikat jest przekierowywany do `CMyExtWindow::OnPaint` rzeczywiste przetwarzania. Jeśli `OnPaint` wskazuje komunikat wymaga dalszego przetwarzania, zostanie komunikat, a następnie nastąpi przekierowanie do mapy wiadomości domyślnej w `CMyBaseWindow`.

Oprócz mapy wiadomości domyślnej, można zdefiniować Mapa alternatywne wiadomości z [ALT_MSG_MAP](#alt_msg_map). Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywne. Poniższy kod przedstawia domyślny mapy komunikatów i jeden komunikat alternatywne mapy, każdy z nich zawierający jedną funkcję programu obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywne. Mapy komunikatów domyślne jest puste.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Należy pamiętać, że jest zawsze dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

Określa wpis w mapie komunikatów.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[in] Nazwa klasy bazowej, zawierający mapie komunikatów.

*msgMapID*<br/>
[in] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT kieruje komunikaty do mapowania alternatywnych wiadomości w klasie bazowej. Wyrazili tej mapie alternatywne wiadomości z [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Do przekierowywania komunikatów do mapy komunikatów domyślną klasę bazową (zadeklarowanych za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP. Aby uzyskać przykład, zobacz [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

Określa wpis w mapie komunikatów.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
[in] Nazwa elementu danych zawierającego mapie komunikatów.

*msgMapID*<br/>
[in] Identyfikator mapy wiadomości.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_ALT_MEMBER Określa, że komunikaty do mapy wiadomości alternatywny element członkowski danych. Wyrazili tej mapie alternatywne wiadomości z [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Do przekierowywania komunikatów do mapy komunikatów domyślny element członkowski danych (zadeklarowanych za pomocą [BEGIN_MSG_MAP](#begin_msg_map)), użyj CHAIN_MSG_MAP_MEMBER. Aby uzyskać przykład, zobacz [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

Określa wpis w mapie komunikatów.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[in] Nazwa klasy bazowej, zawierający mapie komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP kieruje komunikaty do mapy wiadomość domyślną klasę bazową (zadeklarowanych za pomocą [BEGIN_MSG_MAP](#begin_msg_map)). Do przekierowywania komunikatów do mapy komunikatów alternatywne klasę bazową (zadeklarowanych za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Ten przykład ilustruje następujące czynności:

- Jeśli używa procedurę okna `CMyClass`firmy domyślne mapy wiadomości i `OnPaint` nie uchwyt komunikatu, komunikat zostanie skierowany do `CMyBaseClass`firmy domyślne mapy komunikatów do przetworzenia.

- Jeśli procedurę okna przy użyciu pierwszy komunikat alternatywne mapowanie na `CMyClass`, wszystkie komunikaty są kierowane do `CMyBaseClass`firmy domyślne mapy wiadomości.

- Jeśli używa procedurę okna `CMyClass`przez drugi komunikat alternatywne mapy i `OnChar` nie uchwyt komunikatu, komunikat zostanie skierowany do mapy określony komunikat alternatywne w `CMyBaseClass`. `CMyBaseClass` musi mieć zadeklarowany tej mapie komunikatów za pomocą ALT_MSG_MAP(1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

Określa wpis w mapie komunikatów.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
[in] Unikatowy identyfikator obiektu mapie komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_DYNAMIC kieruje komunikaty, w czasie wykonywania, do domyślnego mapy wiadomości w innym obiekcie. Obiekt i jego mapy wiadomości, które są skojarzone z *dynaChainID*, która jest definiowana za pomocą [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Muszą pochodzić z klasy `CDynamicChain` aby można było używać CHAIN_MSG_MAP_DYNAMIC. Aby uzyskać przykład, zobacz [CDynamicChain](../../atl/reference/cdynamicchain-class.md) Przegląd.

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

Określa wpis w mapie komunikatów.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
[in] Nazwa elementu danych zawierającego mapie komunikatów.

### <a name="remarks"></a>Uwagi

CHAIN_MSG_MAP_MEMBER kieruje komunikaty do mapy komunikatów domyślny element członkowski danych (zadeklarowanych za pomocą [BEGIN_MSG_MAP](#begin_msg_map)). Do przekierowywania komunikatów do mapy komunikatów alternatywny element członkowski danych (zadeklarowanych za pomocą [ALT_MSG_MAP](#alt_msg_map)), użyj [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą BEGIN_MSG_MAP. Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Ten przykład ilustruje następujące czynności:

- Jeśli używa procedurę okna `CMyClass`firmy domyślne mapy wiadomości i `OnPaint` nie uchwyt komunikatu, komunikat zostanie skierowany do `m_obj`firmy domyślne mapy komunikatów do przetworzenia.

- Jeśli procedurę okna przy użyciu pierwszy komunikat alternatywne mapowanie na `CMyClass`, wszystkie komunikaty są kierowane do `m_obj`firmy domyślne mapy wiadomości.

- Jeśli używa procedurę okna `CMyClass`przez drugi komunikat alternatywne mapy i `OnChar` nie uchwyt komunikatu, komunikat zostanie skierowany do mapy określony komunikat alternatywne `m_obj`. Klasa `CMyContainedClass` musi zadeklarować tej mapie komunikatów za pomocą ALT_MSG_MAP(1).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości tylko na podstawie powiadomień kodu.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

Określa wpis w mapie komunikatów.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub klawiszy skrótów.

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Mapuje COMMAND_HANDLER [WM_COMMAND](/windows/desktop/menurc/wm-command) komunikatów do funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu. Na przykład:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Żadnej funkcji, które określono w makrze COMMAND_HANDLER musi być zdefiniowany w następujący sposób:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Ustawia mapy wiadomości `bHandled` na wartość TRUE, przed `CommandHandler` jest wywoływana. Jeśli `CommandHandler` nie obsługuje w pełni komunikat, należy ją ustawić `bHandled` na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz COMMAND_HANDLER, można użyć [MESSAGE_HANDLER](#message_handler) do mapy komunikatów WM_COMMAND, bez względu na identyfikator lub kod. W tym przypadku `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` skieruje wszystkich komunikatów WM_COMMAND do `OnHandlerFunction`.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości tylko na podstawie identyfikatora elementu menu, kontrolki lub klawiszy skrótów.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub akceleratora wysyłania komunikatu.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

Podobnie jak [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [WM_COMMAND](/windows/desktop/menurc/wm-command) komunikatów za pomocą kodu określonych powiadomień z szeroką gamę elementów sterujących funkcji pojedynczy program obsługi.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikator elementu menu, formant lub akceleratora wysyłania komunikatu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości z szeroką gamę elementów sterujących funkcji pojedynczy program obsługi.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikator elementu menu, formant lub akceleratora wysyłania komunikatu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

Deklaruje mapą pustego komunikatu.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

DECLARE_EMPTY_MSG_MAP to makro jako udogodnienie, które wywołuje makra [BEGIN_MSG_MAP](#begin_msg_map) i [END_MSG_MAP](#end_msg_map) utworzyć mapę pusty komunikat:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

Udostępnia domyślny program obsługi dla okna podrzędnego (kontrola), który będzie otrzymywał zostaną uwzględnione w wiadomości. Program obsługi prawidłowo przekazują nieobsługiwany wiadomości do `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

Oznacza koniec mapy komunikatów.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Uwagi

Zawsze używaj [BEGIN_MSG_MAP](#begin_msg_map) makra, aby zaznaczyć początek mapy komunikatów. Użyj [ALT_MSG_MAP](#alt_msg_map) do deklarowania mapy kolejnych komunikatów alternatywne.

Należy pamiętać, że jest zawsze dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

Poniższy kod przedstawia domyślny mapy komunikatów i jeden komunikat alternatywne mapy, każdy z nich zawierający jedną funkcję programu obsługi:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

W kolejnym przykładzie pokazano dwa mapy komunikatów alternatywne. Mapy komunikatów domyślne jest puste.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

Przekazuje komunikaty powiadomień do okna nadrzędnego.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część mapy wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

Określa wpis w mapie komunikatów.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*komunikat:*<br/>
[in] Komunikat Windows.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

MESSAGE_HANDLER mapy wiadomości Windows do obsługi funkcji.

Żadnej funkcji, które określono w makrze MESSAGE_HANDLER musi być zdefiniowany w następujący sposób:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Ustawia mapy wiadomości `bHandled` na wartość TRUE, przed `MessageHandler` jest wywoływana. Jeśli `MessageHandler` nie obsługuje w pełni komunikat, należy ją ustawić `bHandled` na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz MESSAGE_HANDLER, można użyć [COMMAND_HANDLER](#command_handler) i [NOTIFY_HANDLER](#notify_handler) do mapowania [WM_COMMAND](/windows/desktop/menurc/wm-command) i [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości , odpowiednio.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

Podobnie jak [MESSAGE_HANDLER](#message_handler), ale mapy zakresu Windows komunikatów do funkcji pojedynczy program obsługi.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgFirst*<br/>
[in] Oznacza początek ciągły zakres komunikatów.

*msgLast*<br/>
[in] Oznacza koniec ciągły zakres komunikatów.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości tylko na podstawie powiadomień kodu.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

Określa wpis w mapie komunikatów.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator formantu wysyłania komunikatu.

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Mapuje NOTIFY_HANDLER [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) komunikatów do funkcji obsługi, na podstawie kodu powiadomienia i identyfikator formantu.

Żadnej funkcji, które określono w makrze NOTIFY_HANDLER musi być zdefiniowany w następujący sposób:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Ustawia mapy wiadomości `bHandled` na wartość TRUE, przed `NotifyHandler` jest wywoływana. Jeśli `NotifyHandler` nie obsługuje w pełni komunikat, należy ją ustawić `bHandled` na wartość FAŁSZ, aby wiadomość wymaga dalszego przetwarzania.

> [!NOTE]
>  Zawsze zaczynają się mapy komunikatów za pomocą [BEGIN_MSG_MAP](#begin_msg_map). Następnie można zadeklarować mapy kolejnych komunikatów alternatywny z [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) — makro oznacza koniec mapie komunikatów. Mapy komunikatów, co musi mieć dokładnie jedno wystąpienie BEGIN_MSG_MAP i END_MSG_MAP.

Oprócz NOTIFY_HANDLER, można użyć [MESSAGE_HANDLER](#message_handler) do mapowania komunikat WM_NOTIFY, bez względu na identyfikator lub kod. W tym przypadku `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` skieruje wszystkich komunikatów WM_NOTIFY `OnHandlerFunction`.

Aby uzyskać więcej informacji o korzystaniu z mapy komunikatów w ATL, zobacz [mapy wiadomości](../../atl/message-maps-atl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości tylko na podstawie kontroli identyfikatora.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator formantu wysyłania komunikatu.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

Podobnie jak [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) komunikatów za pomocą kodu określonych powiadomień z szeroką gamę elementów sterujących funkcji pojedynczy program obsługi.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikator kontrolki, wysyłania wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości z szeroką gamę elementów sterujących funkcji pojedynczy program obsługi.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="remarks"></a>Uwagi

Ten zakres jest oparty na identyfikator kontrolki, wysyłania wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

Odzwierciedla powiadomienia do okna podrzędnego (kontrola), która wysłała je.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Uwagi

Określ to makro jako część okna nadrzędnego, w mapie komunikatów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

Podobnie jak [COMMAND_CODE_HANDLER](#command_code_handler), ale mapuje polecenia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

Podobnie jak [COMMAND_HANDLER](#command_handler), ale mapuje polecenia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub klawiszy skrótów.

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

Podobnie jak [COMMAND_ID_HANDLER](#command_id_handler), ale mapuje polecenia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub klawiszy skrótów.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobnie jak [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapuje polecenia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*Kod*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

Podobnie jak [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje polecenia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

Podobnie jak [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

Podobnie jak [NOTIFY_HANDLER](#notify_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub klawiszy skrótów.

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

Podobnie jak [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikator elementu menu, formant lub klawiszy skrótów.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Podobnie jak [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*ciągłe dostarczanie*<br/>
[in] Kod powiadomienia.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

Podobnie jak [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje powiadomienia odzwierciedlonej z okna nadrzędnego.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Oznacza początek ciągły zakres identyfikatorów kontroli.

*idLast*<br/>
[in] Oznacza koniec ciągły zakres identyfikatorów kontroli.

*FUNC*<br/>
[in] Nazwa funkcji obsługi wiadomości.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
