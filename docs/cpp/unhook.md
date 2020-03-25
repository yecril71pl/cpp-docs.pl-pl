---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: 2a259b80b941e37e0c3040ad55894c114fe4bc82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160531"
---
# <a name="__unhook"></a>__unhook

Deskojarzenie metody obsługi ze zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>Parametry

**&** *SourceClass* `::` *EventMethod* wskaźnik do metody zdarzenia, z której zostanie odłożona metoda obsługi zdarzeń:

- Zdarzenia C++ natywne: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

- Zdarzenia COM: *SourceClass* jest interfejsem źródła zdarzeń, a *EventMethod* jest jedną z jej metod.

- Zdarzenia zarządzane: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

*interface*<br/>
Nazwa interfejsu, która jest odłączana od *odbiornika*, tylko dla odbiorników zdarzeń com, w których parametr *layout_dependent* atrybutu [event_receiver](../windows/attributes/event-receiver.md) ma **wartość true**.

*source*<br/>
Wskaźnik do wystąpienia źródła zdarzeń. W zależności od kodu `type` określonego w `event_receiver`, *Źródło* może być jednym z następujących:

- Natywny wskaźnik obiektu źródła zdarzenia.

- Wskaźnik oparty na `IUnknown`(Źródło COM).

- Wskaźnik obiektu zarządzanego (dla zdarzeń zarządzanych).

**&** *ReceiverClass* `::` `HandlerMethod` wskaźnik do metody obsługi zdarzeń, który ma zostać odpinany ze zdarzenia. Procedura obsługi jest określana jako metoda klasy lub odwołania do tego samego; Jeśli nie określisz nazwy klasy, **__unhook** zakłada, że Klasa jest taka, w której jest wywoływana.

- Zdarzenia C++ natywne: *ReceiverClass* jest klasą odbiorcy zdarzeń, a `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* jest interfejsem odbiorcy zdarzeń, a `HandlerMethod` jest jednym z jej obsługi.

- Zdarzenia zarządzane: *ReceiverClass* jest klasą odbiorcy zdarzeń, a `HandlerMethod` jest programem obsługi.

*odbiorca*(opcjonalnie) wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest Klasa odbiornika lub struktura, w której jest wywoływana **__unhook** .

## <a name="usage"></a>Sposób użycia

Można używać w dowolnym zakresie funkcji, w tym Main, poza klasą odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Użyj funkcji wewnętrznej **__unhook** w odbiorniku zdarzenia, aby usunąć skojarzenie lub "odpina" metodę obsługi z metody zdarzenia.

Istnieją trzy formy **__unhook**. W większości przypadków można użyć pierwszego (czterech argumentów) formularza. Można użyć drugiej (dwóch argumentów) formy **__unhook** tylko dla odbiorcy zdarzeń com; spowoduje to odpinanie całego interfejsu zdarzenia. Możesz użyć trzeciego (jednego argumentu) formularza, aby odpiąć wszystkie delegatów z określonego źródła.

Wartość zwrotna niezerowa wskazuje, że wystąpił błąd (zdarzenia zarządzane spowodują zgłoszenie wyjątku).

Jeśli wywołasz **__unhook** na zdarzeniu i obsłudze zdarzeń, które nie zostały już podłączane, nie będzie żadnego efektu.

W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i sprawdza typ parametru z określoną obsługą.

Z wyjątkiem zdarzeń COM, **__hook** i **__unhook** mogą być wywoływane poza odbiorcą zdarzeń.

Alternatywą dla korzystania z **__unhook** jest użycie operatora-=.

Aby uzyskać informacje na temat kodowania zdarzeń zarządzanych w nowej składni, zobacz [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="example"></a>Przykład

Przykłady można znaleźć [w temacie C++ obsługa zdarzeń w natywnym](../cpp/event-handling-in-native-cpp.md) i [obsłudze zdarzeń w modelu COM](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
