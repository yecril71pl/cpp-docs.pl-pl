---
title: Wyliczenia przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376320"
---
# <a name="concurrency-namespace-enums-amp"></a>Wyliczenia przestrzeni nazw współbieżności (AMP)

|||
|-|-|
|[access_type Wyliczenie](#access_type)|[queuing_mode Wyliczenie](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type Wyliczenie

Typ wyliczenia używany do oznaczania różnych typów dostępu do danych.

```cpp
enum access_type;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`access_type_auto`|Automatycznie wybierz najlepsze `access_type` dla akceleratora.|
|`access_type_none`|Dedykowany. Alokacja jest dostępna tylko na akceleratorze, a nie na procesorze.|
|`access_type_read`|Udostępnionych. Alokacja jest dostępna na akceleratorze i jest czytelna na procesorze.|
|`access_type_read_write`|Udostępnionych. Alokacja jest dostępna na akceleratorze i jest zapisywalna na procesorze.|
|`access_type_write`|Udostępnionych. Alokacja jest dostępna na akceleratorze i jest czytelna i zapisywalna na procesorze.|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode Wyliczenie

Określa tryby kolejkowania obsługiwane w akceleratorze.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`queuing_mode_immediate`|Tryb kolejkowania, który określa, że wszystkie polecenia, na przykład [parallel_for_each Function (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), są wysyłane do odpowiedniego urządzenia akceleratora, gdy tylko powrócą do wywołującego.|
|`queuing_mode_automatic`|Tryb kolejkowania, który określa, że polecenia są umieszczane w kolejce poleceń odpowiadających [accelerator_view](accelerator-view-class.md) obiektowi. Polecenia są wysyłane do urządzenia, gdy wywoływana jest [accelerator_view:flush.](accelerator-view-class.md#flush)|

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
