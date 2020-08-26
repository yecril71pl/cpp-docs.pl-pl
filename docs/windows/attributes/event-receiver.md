---
title: event_receiver (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 7280729a9ae3a054468e1f11bdcc4a563b32effe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845292"
---
# <a name="event_receiver"></a>event_receiver

Tworzy odbiorcę zdarzeń (ujścia).

## <a name="syntax"></a>Składnia

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Wyliczenie jednej z następujących wartości:

- `native` dla niezarządzanego kodu C/C++ (domyślnie dla klas natywnych).

- `com` dla kodu COM. Ta wartość wymaga uwzględnienia następujących plików nagłówkowych:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Określ *layout_dependent* tylko wtedy, gdy `type` = **com**. *layout_dependent* jest wartością logiczną:

- **`true`** oznacza, że podpis delegatów w odbiorcy zdarzeń musi dokładnie pasować do tych, do których są one podłączane w źródle zdarzeń. Nazwy programu obsługi odbiornika zdarzeń muszą być zgodne z nazwami określonymi w odpowiednim interfejsie źródła zdarzenia. Należy użyć, `coclass` gdy *layout_dependent* **`true`** . Jest nieco bardziej wydajny **`true`** .

- **`false`** (ustawienie domyślne) oznacza, że Konwencja wywoływania i Klasa magazynu (wirtualne, statyczne i inne) nie muszą być zgodne z metodą zdarzenia i obsługą; ani nazwy programu obsługi muszą być zgodne z nazwami metod interfejsu źródłowego zdarzenia.

## <a name="remarks"></a>Uwagi

Atrybut **event_receiver** C++ określa, że Klasa lub struktura, do której ma zastosowanie, będzie odbiorcą zdarzeń przy użyciu ujednoliconego modelu zdarzeń Visual C++.

**event_receiver** jest używany z atrybutem [event_source](event-source.md) i słowami kluczowymi [__hook](../../cpp/hook.md) i [__unhook](../../cpp/unhook.md) . Służy `event_source` do tworzenia źródeł zdarzeń. Użyj **`__hook`** w metodach odbiorcy zdarzeń, aby skojarzyć metody odbiornika zdarzeń ("Hook") z zdarzeniami źródła zdarzeń. Użyj **`__unhook`** , aby usunąć skojarzenie ich.

*layout_dependent* jest określona tylko dla odbiorników zdarzeń com ( `type` = **com**). Wartość domyślna dla *layout_dependent* to **`false`** .

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|`coclass` gdy *layout_dependent*=**`true`**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)
