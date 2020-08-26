---
title: event_source (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: bea90020c3ec570149e11db95ff6d6f8fd0a5507
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845305"
---
# <a name="event_source"></a>event_source

Tworzy Źródło zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Wyliczenie jednej z następujących wartości:

- `native` dla niezarządzanego kodu C/C++ (domyślnie dla klas niezarządzanych).

- `com` dla kodu COM. Musisz użyć `coclass` `type` = `com` . Ta wartość wymaga uwzględnienia następujących plików nagłówkowych:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*zoptymalizować*<br/>
Gdy *Typ* to `native` , możesz określić `optimize=size` , aby wskazać, że dla wszystkich zdarzeń w klasie lub (wartość domyślna) istnieje 4-bajtowe miejsce w magazynie (minimum) `optimize=speed` .

*dekorować*<br/>
Gdy *Typ* to `native` , można określić `decorate=false` , aby wskazać, że rozwinięta nazwa w scalonym pliku (. MRG) nie powinna zawierać otaczającej nazwy klasy. [/FX](../../build/reference/fx-merge-injected-code.md) umożliwia generowanie plików. MRG. `decorate=false`, który jest wartością domyślną, powoduje w pełni kwalifikowane nazwy typów w scalonym pliku.

## <a name="remarks"></a>Uwagi

Atrybut **event_source** C++ określa, że Klasa lub struktura, do której ma zastosowanie, będzie źródłem zdarzenia.

**event_source** jest używany w połączeniu z atrybutem [event_receiver](event-receiver.md) i słowem kluczowym [__event](../../cpp/event.md) . Służy `event_receiver` do tworzenia odbiorców zdarzeń. Użyj **`__event`** metod w ramach źródła zdarzeń, aby określić te metody jako zdarzenia.

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**Klasa coclass** , gdy `type`=`com`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)
