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
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337564"
---
# <a name="__unhook"></a>__unhook

Dissociates metody obsługi ze zdarzenia.

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

**&** Wskaźnik *zdarzenia* *SourceClass* `::` A do metody zdarzenia, od którego można odłączyć metodę obsługi zdarzeń:

- Natywne zdarzenia C++: *SourceClass* jest klasą źródła zdarzeń, a *EventMethod* jest zdarzeniem.

- Zdarzenia COM: *SourceClass* jest interfejsem źródłowym zdarzeń, a *Metoda EventMethod* jest jedną z jego metod.

- Zdarzenia zarządzane: *SourceClass* jest klasą źródła zdarzenia, a *EventMethod* jest zdarzeniem.

*interface*<br/>
Nazwa interfejsu odłączona od *odbiornika,* tylko dla odbiorników zdarzeń COM, w których *layout_dependent* parametr atrybutu [event_receiver](../windows/attributes/event-receiver.md) jest **true**.

*Źródła*<br/>
Wskaźnik do wystąpienia źródła zdarzenia. W zależności `type` od `event_receiver`kodu określonego w programie *źródło* może być jedną z następujących czynności:

- Wskaźnik macierzystego obiektu źródłowego zdarzenia.

- Wskaźnik `IUnknown`oparty na wskaźniku (źródło COM).

- Wskaźnik obiektu zarządzanego (dla zdarzeń zarządzanych).

**&***Wskaźnik ReceiverClass* `::` `HandlerMethod` A do metody obsługi zdarzeń, która ma zostać odłączona od zdarzenia. Program obsługi jest określony jako metoda klasy lub odwołanie do tego samego; jeśli nie określisz nazwę klasy, **__unhook** zakłada, że klasa jest tym, w którym jest wywoływana.

- Natywne zdarzenia C++: *ReceiverClass* jest klasą odbiornika zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* jest interfejsem odbiornika zdarzeń i `HandlerMethod` jest jednym z jego programów obsługi.

- Zdarzenia zarządzane: *ReceiverClass* jest klasą odbiornika zdarzeń i `HandlerMethod` jest programem obsługi.

*odbiornik*(opcjonalnie) Wskaźnik do wystąpienia klasy odbiornika zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest klasa lub struktura odbiornika, w której wywoływana jest **__unhook.**

## <a name="usage"></a>Sposób użycia

Może być używany w dowolnym zakresie funkcji, w tym głównym, poza klasą odbiornika zdarzeń.

## <a name="remarks"></a>Uwagi

Użyj funkcji wewnętrznej **__unhook** w odbiorniku zdarzeń, aby odłączyć lub "odłączyć" metodę obsługi od metody zdarzenia.

Istnieją trzy formy **__unhook**. W większości przypadków można użyć formularza pierwszego (czterech argumentów). Można użyć drugiej (dwuksymentowej) formy **__unhook** tylko dla odbiornika zdarzeń COM; spowoduje to odłączyć cały interfejs zdarzenia. Można użyć trzeciego formularza (jeden argument), aby odłączyć wszystkich delegatów z określonego źródła.

Wartość zwracana niezerowa wskazuje, że wystąpił błąd (zdarzenia zarządzane zdadzą wyjątek).

Jeśli wywołasz **__unhook** na program obsługi zdarzeń i zdarzeń, które nie są jeszcze podłączone, nie będzie miało wpływu.

W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i sprawdza typ parametru za pomocą określonego programu obsługi.

Z wyjątkiem zdarzeń **COM, __hook** i **__unhook** można wywołać poza odbiornikiem zdarzeń.

Alternatywą dla korzystania **z __unhook** jest użycie operatora -= .

Aby uzyskać informacje na temat kodowania zdarzeń zarządzanych w nowej składni, zobacz [zdarzenie](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Klasa szablonu lub struktura nie może zawierać zdarzeń.

## <a name="example"></a>Przykład

Zobacz [obsługa zdarzeń w natywnych C++](../cpp/event-handling-in-native-cpp.md) i obsługi zdarzeń w [com](../cpp/event-handling-in-com.md) dla przykładów.

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
