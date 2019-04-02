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
ms.openlocfilehash: e8f42c35024995c026ae10fc7f0ab3db77d1e5dc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769527"
---
# <a name="unhook"></a>__unhook

Dissociates metody obsługi zdarzeń.

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

**&** *SourceClass* `::` *EventMethod* wskaźnik do metody zdarzeń, z którego odczepić metody obsługi zdarzeń:

- Zdarzenia natywnego języka C++: *SourceClass* jest klasie źródła zdarzeń i *EventMethod* jest zdarzenie.

- Zdarzenia COM: *SourceClass* interfejs źródła zdarzeń i *EventMethod* jest jednym z jej metody.

- Zdarzenia zarządzane: *SourceClass* jest klasie źródła zdarzeń i *EventMethod* jest zdarzenie.

*interface*<br/>
Nazwa interfejsu, jest unhooked z *odbiorcy*, tylko w przypadku odbiorników zdarzeń COM, w którym *layout_dependent* parametru [event_receiver](../windows/attributes/event-receiver.md) atrybut jest **true**.

*source*<br/>
Wskaźnik na wystąpienie źródła zdarzeń. W zależności od kodu `type` określonych w `event_receiver`, *źródła* może być jedną z następujących czynności:

- Wskaźnik obiektu źródła zdarzeń macierzystych.

- `IUnknown`-Oparte wskaźnikiem (źródło modelu COM).

- Wskaźnik zarządzanego obiektu (w przypadku zarządzanych zdarzeń).

**&** *ReceiverClass* `::` `HandlerMethod` wskaźnik do metody obsługi zdarzeń jako unhooked ze zdarzenia. Program obsługi jest określony jako metoda klasy lub odwołanie do tej samej; Jeśli nie określisz nazwy klasy, **__unhook** przyjęto założenie, klasy, która ma być, że w którym jest wywoływana.

- Zdarzenia natywnego języka C++: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* interfejs odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługę.

- Zdarzenia zarządzane: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

*odbiornik*(opcjonalnie) wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest odbiorcy klasy lub struktury, w którym **__unhook** jest wywoływana.

## <a name="usage"></a>Sposób użycia

Może być użycie w zakresie dowolnej funkcji, łącznie z głównym, poza klasy odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Funkcja wewnętrzna **__unhook** w odbiorcy zdarzeń, aby usunąć skojarzenie lub "odczepić" metodę programu obsługi z metody zdarzeń.

Istnieją trzy rodzaje **__unhook**. W większości przypadków można użyć pierwszy formy (4 argument). Można użyć drugiej formy (dwuargumentową) **__unhook** tylko dla odbiorcy zdarzenia COM; to unhooks interfejsu całe zdarzenie. Trzecia formą (one-argument —) umożliwia Odpięcie wszystkich obiektów delegowanych pochodzących z określonego źródła.

Wartość różną od zera, zwracana wartość wskazuje na to, że wystąpił błąd (zdarzenia zarządzane spowoduje zgłoszenie wyjątku).

Jeśli wywołasz **__unhook** na zdarzenia i program obsługi zdarzeń, które nie są już podłączone odniesie żadnego skutku.

W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i czy parametr typu sprawdzenie z określonym programem obsługi.

Z wyjątkiem zdarzeń COM **__hook** i **__unhook** może być wywołana poza odbiorcy zdarzeń.

Alternatywa dla użycia **__unhook** jest użycie operatora-=.

Aby uzyskać informacji na temat kodowania zarządzanych zdarzeń w nowej składni, zobacz [zdarzeń](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="example"></a>Przykład

Zobacz [zdarzenie obsługi w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [zdarzenie obsługi w modelu COM](../cpp/event-handling-in-com.md) przykładów.

## <a name="see-also"></a>Zobacz także

[słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)