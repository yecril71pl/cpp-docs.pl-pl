---
title: event_receiver (C++ atrybut com)
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
ms.openlocfilehash: 9653a0b5c756857d92914496b9c5c6f8aee56ebb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167085"
---
# <a name="event_receiver"></a>event_receiver

Tworzy odbiorcę zdarzeń (ujścia).

## <a name="syntax"></a>Składnia

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Wyliczenie jednej z następujących wartości:

- `native` dla niezarządzanegoC++ kodu C/Code (domyślnie dla klas natywnych).

- `com` dla kodu COM. Ta wartość wymaga uwzględnienia następujących plików nagłówkowych:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Określ *layout_dependent* tylko wtedy, gdy `type`=**com**. *layout_dependent* jest wartością logiczną:

- **prawda** oznacza, że podpis delegatów w odbiorcy zdarzeń musi dokładnie pasować do tych, do których są one podłączane w źródle zdarzeń. Nazwy programu obsługi odbiornika zdarzeń muszą być zgodne z nazwami określonymi w odpowiednim interfejsie źródła zdarzenia. Należy użyć `coclass`, gdy *layout_dependent* ma **wartość true**. Określenie **wartości true**jest nieco bardziej wydajne.

- **false** (domyślnie) oznacza, że Konwencja wywoływania i Klasa magazynu (wirtualne, statyczne i inne) nie muszą być zgodne z metodą zdarzenia i obsługą; ani nazwy programu obsługi muszą być zgodne z nazwami metod interfejsu źródłowego zdarzenia.

## <a name="remarks"></a>Uwagi

Atrybut **event_receiver** C++ określa, że Klasa lub struktura, do której ma zastosowanie, będzie odbiorcą zdarzeń przy użyciu C++ ujednoliconego modelu zdarzeń.

**event_receiver** jest używany z atrybutem [event_source](event-source.md) i słowami kluczowymi [__hook](../../cpp/hook.md) i [__unhook](../../cpp/unhook.md) . Użyj `event_source`, aby utworzyć źródła zdarzeń. Użyj **__hook** w metodach odbiorcy zdarzeń, aby skojarzyć metody odbiornika zdarzeń ("Hook") z zdarzeniami źródła zdarzeń. Użyj **__unhook** , aby usunąć ich skojarzenie.

*layout_dependent* jest określony tylko dla odbiorników zdarzeń COM (`type`=**com**). Wartość domyślna dla *layout_dependent* ma **wartość false**.

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|`coclass`, gdy *layout_dependent*=**true**|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)
