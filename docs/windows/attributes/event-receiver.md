---
title: event_receiver (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95e5d65d437b60f6421978682997067d8f53a3d5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073958"
---
# <a name="eventreceiver"></a>event_receiver

Tworzy odbiorca zdarzenia (ujścia).

## <a name="syntax"></a>Składnia

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Wyliczenie jednego z następujących wartości:

- `native` dla niezarządzanego kodu C/C++ (domyślnie dla macierzystych klas).

- `com` dla kodu COM. Ta wartość wymaga, że zawrzesz następujące pliki nagłówków:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Określ *layout_dependent* tylko wtedy, gdy `type` = **com**. *layout_dependent* jest wartością logiczną:

- **wartość true,** oznacza, że podpis delegatów w przypadku odbiornika musi dokładnie odpowiadać tych, do których są podłączone w zdarzeniu źródła. Nazwy programów obsługi odbiorcy zdarzeń muszą być zgodne nazwy określone w interfejsie źródła istotnych zdarzeń. Należy użyć `coclass` podczas *layout_dependent* jest **true**. Jest nieco bardziej efektywne, aby określić **true**.

- **FALSE** (ustawienie domyślne) oznacza, że wywołania Konwencji i klasy pamięci (wirtualne, statyczne i inne) ani nie musi odpowiadać metody zdarzeń i obsługi; czy nazwy programów obsługi muszą odpowiadać nazwom metody interfejsu źródła zdarzeń.

## <a name="remarks"></a>Uwagi

**Event_receiver** atrybut C++ Określa, że klasy lub struktury, do którego jest stosowana będzie odbiorca zdarzenia, przy użyciu modelu zdarzeń ujednoliconego Visual C++.

**event_receiver** jest używana z [event_source](event-source.md) atrybutu i [__hook](../../cpp/hook.md) i [__unhook](../../cpp/unhook.md) słów kluczowych. Użyj `event_source` utworzyć źródła zdarzeń. Użyj **__hook** w metodach odbiorca zdarzenia, aby skojarzyć metody odbiorcy zdarzeń ("hook") na potrzeby zdarzeń źródła zdarzeń. Użyj **__unhook** usunąć ich skojarzenia.

*layout_dependent* jest określana tylko dla odbiorcy zdarzeń COM (`type`=**com**). Wartość domyślna dla *layout_dependent* jest **false**.

> [!NOTE]
> Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|`coclass` gdy *layout_dependent*=**true**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)