---
title: event_source (C++ atrybut com)
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
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167072"
---
# <a name="event_source"></a>event_source

Tworzy Źródło zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Wyliczenie jednej z następujących wartości:

- `native` dla niezarządzanegoC++ kodu C/Code (domyślnie dla klas niezarządzanych).

- `com` dla kodu COM. Należy użyć `coclass`, gdy `type`=`com`. Ta wartość wymaga uwzględnienia następujących plików nagłówkowych:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optymalizuj*<br/>
Gdy *Typ* jest `native`, można określić `optimize=size`, aby wskazać, że jest 4-bajtowy magazyn (minimum) dla wszystkich zdarzeń w klasie lub `optimize=speed` (wartość domyślna), aby wskazać, że istnieją 4 * (liczba zdarzeń) bajty magazynu.

*dekorować*<br/>
Gdy *Typ* jest `native`, można określić `decorate=false`, aby wskazać, że rozwinięta nazwa w pliku scalonego (. MRG) nie powinna zawierać otaczającej nazwy klasy. [/FX](../../build/reference/fx-merge-injected-code.md) umożliwia generowanie plików. MRG. `decorate=false`, która jest wartością domyślną, powoduje w pełni kwalifikowane nazwy typów w scalonym pliku.

## <a name="remarks"></a>Uwagi

Atrybut **event_source** C++ określa, że Klasa lub struktura, do której ma zastosowanie, będzie źródłem zdarzenia.

**event_source** jest używany w połączeniu z atrybutem [event_receiver](event-receiver.md) i słowem kluczowym [__event](../../cpp/event.md) . Użyj `event_receiver`, aby utworzyć odbiorców zdarzeń. Użyj **__event** metod w źródle zdarzenia, aby określić te metody jako zdarzenia.

> [!NOTE]
> Klasa lub struktura z szablonem nie może zawierać zdarzeń.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**Klasa coclass** podczas `type`=`com`|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atrybuty klasy](class-attributes.md)
