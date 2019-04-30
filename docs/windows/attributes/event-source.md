---
title: event_source (C++ atrybutów COM)
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
ms.openlocfilehash: 81eba3c032a3556d1c69ad02652455ebc07ab6be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409643"
---
# <a name="eventsource"></a>event_source

Tworzy źródła zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Wyliczenie jednego z następujących wartości:

- `native` dla niezarządzanego kodu C/C++ (wartość domyślna dla klasy niezarządzane).

- `com` dla kodu COM. Należy użyć `coclass` podczas `type` = `com`. Ta wartość wymaga, że zawrzesz następujące pliki nagłówków:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optymalizuj*<br/>
Gdy *typu* jest `native`, można określić `optimize=size`, aby wskazać, że istnieje 4 bajty pamięci masowej (minimum) dla wszystkich zdarzeń w klasie lub `optimize=speed` (ustawienie domyślne), aby wskazać, że jest 4 * (liczba zdarzeń) bajtów magazynu.

*dekoracji*<br/>
Gdy *typu* jest `native`, można określić `decorate=false`, aby wskazać, że rozwiniętej nazwy w pliku scalonego (.mrg) nie powinna zawierać nazwę klasy otaczającej. [/FX](../../build/reference/fx-merge-injected-code.md) umożliwia generowanie plików .mrg. `decorate=false`, która jest wartością domyślną, wyniki w pełni kwalifikowanego typu nazwy w scalony plik.

## <a name="remarks"></a>Uwagi

**Event_source** C++ atrybut określa, że klasy lub struktury, do którego jest stosowana będzie źródła zdarzenia.

**event_source** jest używany w połączeniu z [event_receiver](event-receiver.md) atrybutu i [__event](../../cpp/event.md) — słowo kluczowe. Użyj `event_receiver` do tworzenia odbiorcy zdarzeń. Użyj **__event** metod w źródle zdarzenia do określenia tych metod jako zdarzenia.

> [!NOTE]
> Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**Klasa coclass** po `type`=`com`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)