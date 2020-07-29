---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: 5a0eaf0a3bc0617dbcd1f43805af8a95291e7e47
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188170"
---
# <a name="__hook"></a>__hook

Kojarzy metodę procedury obsługi ze zdarzeniem.

## <a name="syntax"></a>Składnia

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>Parametry

*&SourceClass:: EventMethod*<br/>
Wskaźnik do metody zdarzenia, do której zostanie poddana metoda obsługi zdarzeń:

- Natywne zdarzenia języka C++: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

- Zdarzenia COM: *SourceClass* jest interfejsem źródła zdarzeń, a *EventMethod* jest jedną z jej metod.

- Zdarzenia zarządzane: *SourceClass* jest klasą źródłową zdarzenia, a *EventMethod* to zdarzenie.

*interfejsu*<br/>
Nazwa interfejsu, który jest podłączany do *odbiornika*, tylko dla odbiorników zdarzeń com, w których parametr *layout_dependent* atrybutu [event_receiver](../windows/attributes/event-receiver.md) ma wartość **`true`** .

*zewnętrz*<br/>
Wskaźnik do wystąpienia źródła zdarzeń. W zależności od kodu `type` określonego w `event_receiver` , *Źródło* może być jednym z następujących:

- Natywny wskaźnik obiektu źródła zdarzenia.

- `IUnknown`Wskaźnik oparty na (źródle com).

- Wskaźnik obiektu zarządzanego (dla zdarzeń zarządzanych).

*&ReceiverClass:: HandlerMethod*<br/>
Wskaźnik do metody obsługi zdarzeń, który ma zostać poddany zdarzeniu. Procedura obsługi jest określana jako metoda klasy lub odwołania do tego samego; Jeśli nie określisz nazwy klasy, przyjmuje się, **`__hook`** że Klasa jest taka, w której jest wywoływana.

- Natywne zdarzenia języka C++: *ReceiverClass* jest klasą odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* jest interfejsem odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługi.

- Zdarzenia zarządzane: *ReceiverClass* jest klasą odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

*nadajnik*<br/>
Obowiązkowe Wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest Klasa odbiornika lub struktura, w której **`__hook`** jest wywoływana.

## <a name="usage"></a>Sposób użycia

Można używać w dowolnym zakresie funkcji, w tym Main, poza klasą odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Użyj funkcji wewnętrznej **`__hook`** w odbiorniku zdarzenia, aby skojarzyć lub podpiąć metodę procedury obsługi przy użyciu metody zdarzenia. Określony program obsługi jest następnie wywoływany, gdy źródło zgłasza określone zdarzenie. Można podłączyć kilka programów obsługi do pojedynczego zdarzenia lub podłączyć kilka zdarzeń do jednego programu obsługi.

Istnieją dwie formy **`__hook`** . W większości przypadków można użyć pierwszego (czterech argumentów) formularza, w szczególności dla odbiorników zdarzeń COM, w których parametr *layout_dependent* atrybutu [event_receiver](../windows/attributes/event-receiver.md) ma wartość **`false`** .

W takich przypadkach nie trzeba dołączać wszystkich metod w interfejsie przed wyzwoleniem zdarzenia na jednej z metod; należy podłączać tylko metodę obsługującą zdarzenie. Można użyć drugiego (dwóch argumentów) formularza **`__hook`** tylko dla odbiorcy zdarzeń com, w którym *layout_dependent* **= true**.

**`__hook`** Zwraca wartość długą. Wartość zwrotna niezerowa wskazuje, że wystąpił błąd (zdarzenia zarządzane zgłasza wyjątek).

Kompilator sprawdza obecność zdarzenia i sygnatura zdarzenia zgadza się z podpisem delegata.

Z wyjątkiem zdarzeń COM **`__hook`** i **`__unhook`** mogą być wywoływane poza odbiorcą zdarzeń.

Alternatywą dla użycia **`__hook`** jest użycie operatora + =.

Aby uzyskać informacje na temat kodowania zdarzeń zarządzanych w nowej składni, zobacz [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="example"></a>Przykład

Zobacz [Obsługa zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [Obsługa zdarzeń w modelu COM](../cpp/event-handling-in-com.md) dla przykładów.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
