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
ms.openlocfilehash: 84df5ad0ff27e6b09134b0f92f14f8e9b6fdc817
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233577"
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

**&***SourceClass* `::` *EventMethod* Wskaźnik do metody zdarzenia, z której zostanie odłożona metoda obsługi zdarzeń:

- Natywne zdarzenia języka C++: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

- Zdarzenia COM: *SourceClass* jest interfejsem źródła zdarzeń, a *EventMethod* jest jedną z jej metod.

- Zdarzenia zarządzane: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

*interfejsu*<br/>
Nazwa interfejsu, która jest odłączana od *odbiornika*, tylko dla odbiorników zdarzeń com, w których parametr *layout_dependent* atrybutu [event_receiver](../windows/attributes/event-receiver.md) ma wartość **`true`** .

*zewnętrz*<br/>
Wskaźnik do wystąpienia źródła zdarzeń. W zależności od kodu `type` określonego w `event_receiver` , *Źródło* może być jednym z następujących:

- Natywny wskaźnik obiektu źródła zdarzenia.

- `IUnknown`Wskaźnik oparty na (źródle com).

- Wskaźnik obiektu zarządzanego (dla zdarzeń zarządzanych).

**&***ReceiverClass* `::` `HandlerMethod`Wskaźnik do metody obsługi zdarzeń, który ma zostać odpinany ze zdarzenia. Procedura obsługi jest określana jako metoda klasy lub odwołania do tego samego; Jeśli nie określisz nazwy klasy, przyjmuje się, **`__unhook`** że Klasa jest taka, w której jest wywoływana.

- Natywne zdarzenia języka C++: *ReceiverClass* jest klasą odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* jest interfejsem odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługi.

- Zdarzenia zarządzane: *ReceiverClass* jest klasą odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

*odbiorca*(opcjonalnie) wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest Klasa odbiornika lub struktura, w której **`__unhook`** jest wywoływana.

## <a name="usage"></a>Sposób użycia

Można używać w dowolnym zakresie funkcji, w tym Main, poza klasą odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Użyj funkcji wewnętrznej **`__unhook`** w odbiorniku zdarzenia, aby usunąć skojarzenie lub "odpina" metodę obsługi z metody zdarzenia.

Istnieją trzy formy **`__unhook`** . W większości przypadków można użyć pierwszego (czterech argumentów) formularza. Można użyć drugiego (dwóch argumentów) formy **`__unhook`** tylko dla odbiorcy zdarzeń com; spowoduje to odpinanie całego interfejsu zdarzenia. Możesz użyć trzeciego (jednego argumentu) formularza, aby odpiąć wszystkie delegatów z określonego źródła.

Wartość zwrotna niezerowa wskazuje, że wystąpił błąd (zdarzenia zarządzane spowodują zgłoszenie wyjątku).

Jeśli wywołasz **`__unhook`** zdarzenia i procedurę obsługi zdarzeń, które nie zostały jeszcze podłączane, nie będzie to miało żadnego efektu.

W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i sprawdza typ parametru z określoną obsługą.

Z wyjątkiem zdarzeń COM **`__hook`** i **`__unhook`** mogą być wywoływane poza odbiorcą zdarzeń.

Alternatywą dla użycia **`__unhook`** jest użycie operatora-=.

Aby uzyskać informacje na temat kodowania zdarzeń zarządzanych w nowej składni, zobacz [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="example"></a>Przykład

Zobacz [Obsługa zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [Obsługa zdarzeń w modelu COM](../cpp/event-handling-in-com.md) dla przykładów.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
