---
title: __unhook | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3efdce5bb7a9ab093a53b6a005492aecd509f560
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117299"
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

- Zarządzanych zdarzeń: *SourceClass* jest klasie źródła zdarzeń i *EventMethod* jest zdarzenie.

*interface*<br/>
Nazwa interfejsu, jest unhooked z *odbiorcy*, tylko w przypadku odbiorników zdarzeń COM, w którym *layout_dependent* parametru [event_receiver](../windows/event-receiver.md) atrybut jest **true**.

*source*<br/>
Wskaźnik na wystąpienie źródła zdarzeń. W zależności od kodu `type` określonych w `event_receiver`, *źródła* może być jedną z następujących czynności:

- Wskaźnik obiektu źródła zdarzeń macierzystych.

- `IUnknown`-Oparte wskaźnikiem (źródło modelu COM).

- Wskaźnik zarządzanego obiektu (w przypadku zarządzanych zdarzeń).

**&** *ReceiverClass* `::` `HandlerMethod` wskaźnik do metody obsługi zdarzeń jako unhooked ze zdarzenia. Program obsługi jest określony jako metoda klasy lub odwołanie do tej samej; Jeśli nie określisz nazwy klasy, **__unhook** przyjęto założenie, klasy, która ma być, że w którym jest wywoływana.

- Zdarzenia natywnego języka C++: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* interfejs odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługę.

- Zarządzanych zdarzeń: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

*odbiornik*(opcjonalnie) wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest odbiorcy klasy lub struktury, w którym **__unhook** jest wywoływana.

## <a name="usage"></a>Użycie

Może być użycie w zakresie dowolnej funkcji, łącznie z głównym, poza klasy odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Funkcja wewnętrzna **__unhook** w odbiorcy zdarzeń, aby usunąć skojarzenie lub "odczepić" metodę programu obsługi z metody zdarzeń.

Istnieją trzy rodzaje **__unhook**. W większości przypadków można użyć pierwszy formy (4 argument). Można użyć drugiej formy (dwuargumentową) **__unhook** tylko dla odbiorcy zdarzenia COM; to unhooks interfejsu całe zdarzenie. Trzecia formą (one-argument —) umożliwia Odpięcie wszystkich obiektów delegowanych pochodzących z określonego źródła.

Wartość różną od zera, zwracana wartość wskazuje na to, że wystąpił błąd (zdarzenia zarządzane spowoduje zgłoszenie wyjątku).

Jeśli wywołasz **__unhook** na zdarzenia i program obsługi zdarzeń, które nie są już podłączone odniesie żadnego skutku.

W czasie kompilacji kompilator sprawdza, czy zdarzenie istnieje i czy parametr typu sprawdzenie z określonym programem obsługi.

Z wyjątkiem zdarzeń COM **__hook** i **__unhook** może być wywołana poza odbiorcy zdarzeń.

Alternatywa dla użycia **__unhook** jest użycie operatora-=.

Aby uzyskać informacji na temat kodowania zarządzanych zdarzeń w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).

> [!NOTE]
>  Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="example"></a>Przykład

Zobacz [zdarzenie obsługi w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [zdarzenie obsługi w modelu COM](../cpp/event-handling-in-com.md) przykładów.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/event-source.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)