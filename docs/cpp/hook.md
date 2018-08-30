---
title: __hook | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __hook_cpp
dev_langs:
- C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd5ebd1b70476fd4248d3e309dec967ea471cf0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197400"
---
# <a name="hook"></a>__hook

Kojarzy metody obsługi ze zdarzeniem.

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

*& SourceClass::EventMethod*<br/>
Wskaźnik do metody zdarzeń, do której należy dołączyć metody obsługi zdarzeń:

- Zdarzenia natywnego języka C++: *SourceClass* jest klasie źródła zdarzeń i *EventMethod* jest zdarzenie.

- Zdarzenia COM: *SourceClass* interfejs źródła zdarzeń i *EventMethod* jest jednym z jej metody.

- Zarządzanych zdarzeń: *SourceClass* jest klasie źródła zdarzeń i *EventMethod* jest zdarzenie.

*interface*<br/>
Nazwa interfejsu, są podłączone do *odbiorcy*, tylko w przypadku odbiorników zdarzeń COM, w którym *layout_dependent* parametru [event_receiver](../windows/event-receiver.md) atrybut jest **true**.

*source*<br/>
Wskaźnik na wystąpienie źródła zdarzeń. W zależności od kodu `type` określonych w `event_receiver`, *źródła* może być jedną z następujących czynności:

- Wskaźnik obiektu źródła zdarzeń macierzystych.

- `IUnknown`-Oparte wskaźnikiem (źródło modelu COM).

- Wskaźnik zarządzanego obiektu (w przypadku zarządzanych zdarzeń).

*& ReceiverClass::HandlerMethod*<br/>
Wskaźnik do metody obsługi zdarzeń, aby być dołączane do zdarzenia. Program obsługi jest określony jako metoda klasy lub odwołanie do tej samej; Jeśli nie określisz nazwy klasy, **__hook** przyjęto założenie, klasy, która ma być, że w którym jest wywoływana.

- Zdarzenia natywnego języka C++: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

- Zdarzenia COM: *ReceiverClass* interfejs odbiorcy zdarzeń i `HandlerMethod` jest jednym z jego obsługę.

- Zarządzanych zdarzeń: *ReceiverClass* jest klasy odbiorcy zdarzeń i `HandlerMethod` jest programem obsługi.

*odbiornik* (opcjonalnie)<br/>
Wskaźnik do wystąpienia klasy odbiorcy zdarzeń. Jeśli odbiornik nie zostanie określony, wartością domyślną jest odbiorcy klasy lub struktury, w którym **__hook** jest wywoływana.

## <a name="usage"></a>Użycie

Może być użycie w zakresie dowolnej funkcji, łącznie z głównym, poza klasy odbiorcy zdarzeń.

## <a name="remarks"></a>Uwagi

Funkcja wewnętrzna **__hook** w odbiorcy zdarzeń, aby skojarzyć lub utworzenie punktu zaczepienia metody obsługi, za pomocą metody zdarzeń. Określona Obsługa następnie jest wywoływana, gdy źródło zgłasza określonego zdarzenia. Można podłączyć kilka programów obsługi pojedynczego zdarzenia lub podłączyć kilka zdarzeń do jednego programu obsługi.

Istnieją dwa rodzaje **__hook**. Pierwszy formularz (4 argument), w większości przypadków można użyć w szczególności dla odbiorcy zdarzeń COM, w którym *layout_dependent* parametru [event_receiver](../windows/event-receiver.md) atrybut jest **false** .

W takiej sytuacji nie trzeba podłączyć wszystkie metody w interfejsie przed wyzwoleniem zdarzenia na jednej z metod; metody obsługi zdarzenia musi być dołączane. Można użyć drugiej formy (dwuargumentową) **__hook** tylko dla odbiorcy zdarzenia COM, w którym *layout_dependent* **= true**.

**__hook** zwraca wartość typu long. Wartość różną od zera zwracana wartość wskazuje, że wystąpił błąd (zdarzenia zarządzane throw wyjątku).

Kompilator sprawdza istnienie zdarzeń oraz że podpis zdarzeń są zgodne z podpis delegata.

Z wyjątkiem zdarzeń COM **__hook** i **__unhook** może być wywołana poza odbiorcy zdarzeń.

Alternatywa dla użycia **__hook** polega na użyciu += operator.

Aby uzyskać informacji na temat kodowania zarządzanych zdarzeń w nowej składni, zobacz [zdarzeń](../windows/event-cpp-component-extensions.md).

> [!NOTE]
> Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="example"></a>Przykład

Zobacz [zdarzenie obsługi w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md) i [zdarzenie obsługi w modelu COM](../cpp/event-handling-in-com.md) przykładów.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
[event_source](../windows/event-source.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
