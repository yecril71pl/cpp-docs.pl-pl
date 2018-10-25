---
title: event_source (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41a757ccd70fe95ce82f90b1128985986e3722b0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057819"
---
# <a name="eventsource"></a>event_source

Tworzy źródła zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
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

**Event_source** atrybut C++ Określa, że klasy lub struktury, do którego jest stosowana będzie źródła zdarzenia.

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

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)