---
title: Wyliczenia przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: d78299a9ce47760e6b1340c69d8be699a5eed8a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433578"
---
# <a name="concurrency-namespace-enums-amp"></a>Wyliczenia przestrzeni nazw współbieżności (AMP)

|||
|-|-|
|[access_type — wyliczenie](#access_type)|[queuing_mode — wyliczenie](#queuing_mode)|

##  <a name="access_type"></a>  access_type — wyliczenie

Typ wyliczeniowy używany do oznaczania różnych typów dostępu do danych.

```
enum access_type;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`access_type_auto`|Automatycznie wybiera najlepsze `access_type` dla akceleratora.|
|`access_type_none`|W wersji dedykowanej. Przydział jest dostępny tylko na akceleratorze, nie na CPU.|
|`access_type_read`|Udostępnione. Przydział jest dostępny na akceleratorze i czytelny na CPU.|
|`access_type_read_write`|Udostępnione. Przydział jest dostępny na akceleratorze i zapisywalny na CPU.|
|`access_type_write`|Udostępnione. Przydział jest dostępny na akceleratorze i czytelny i zapisywalny na CPU.|

##  <a name="queuing_mode"></a>  queuing_mode — wyliczenie

Określa tryby kolejkowania, które są obsługiwane w akceleratorze.

```
enum queuing_mode;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`queuing_mode_immediate`|Tryb kolejkowania, który określa, że wszelkie polecenia, na przykład [parallel_for_each — funkcja (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), są wysyłane do odpowiadającego urządzenia akceleratora, jak tylko powrócą do wywołującego.|
|`queuing_mode_automatic`|Tryb kolejkowania, który określa, że polecenia są kolejkowane w kolejce poleceń, który odpowiada [accelerator_view](accelerator-view-class.md) obiektu. Polecenia są wysyłane do urządzenia po [accelerator_view::flush](accelerator-view-class.md#flush) jest wywoływana.|

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
