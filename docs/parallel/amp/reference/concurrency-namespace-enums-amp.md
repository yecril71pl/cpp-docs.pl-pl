---
title: Wyliczenia przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 3dbb8f265706f7a4c369c80d3050cd1bfd2f5acb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845097"
---
# <a name="concurrency-namespace-enums-amp"></a>Wyliczenia przestrzeni nazw współbieżności (AMP)

[access_type, Wyliczenie](#access_type)\
[queuing_mode, Wyliczenie](#queuing_mode)

## <a name="access_type-enumeration"></a><a name="access_type"></a> access_type, Wyliczenie

Typ wyliczeniowy używany do określenia różnych typów dostępu do danych.

```cpp
enum access_type;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`access_type_auto`|Automatycznie wybieraj najlepsze `access_type` dla akceleratora.|
|`access_type_none`|Personel. Alokacja jest dostępna tylko dla akceleratora, a nie na PROCESORze.|
|`access_type_read`|Udostępniać. Przydział jest dostępny na akceleratorze i można go odczytać na PROCESORze.|
|`access_type_read_write`|Udostępniać. Alokacja jest dostępna w akceleratorze i jest zapisywalna na PROCESORze.|
|`access_type_write`|Udostępniać. Przydział jest dostępny na akceleratorze i można go odczytać i zapisać na procesorze CPU.|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a> queuing_mode, Wyliczenie

Określa tryby kolejkowania, które są obsługiwane w akceleratorze.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`queuing_mode_immediate`|Tryb kolejkowania, który określa, że wszystkie polecenia, na przykład [funkcja parallel_for_each (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each), są wysyłane do odpowiedniego urządzenia akceleratora zaraz po powrocie do obiektu wywołującego.|
|`queuing_mode_automatic`|Tryb kolejkowania, który określa, że polecenia są umieszczane w kolejce poleceń, która odpowiada obiektowi [accelerator_view](accelerator-view-class.md) . Polecenia są wysyłane do urządzenia, gdy zostanie wywołane [accelerator_view:: Flush](accelerator-view-class.md#flush) .|

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
