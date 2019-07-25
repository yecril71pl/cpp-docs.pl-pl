---
title: '&lt;wątek&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460073"
---
# <a name="ltthreadgt"></a>&lt;wątek&gt;

Dołącz standardowy wątek nagłówka \<>, aby zdefiniować **wątek** klasy i różne funkcje pomocnicze.

## <a name="syntax"></a>Składnia

```cpp
#include <thread>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, ten nagłówek jest zablokowany.

`__STDCPP_THREADS__` Makro jest zdefiniowane jako wartość różna od zera, aby wskazać, że wątki są obsługiwane przez ten nagłówek.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[thread, klasa](../standard-library/thread-class.md)|Definiuje obiekt, który jest używany do obserwowania wątku wykonywania w aplikacji i zarządzania nim.|

### <a name="public-structures"></a>Struktury publiczne

|Nazwa|Opis|
|----------|-----------------|
|[hash, struktura (Standardowa biblioteka C++)](../standard-library/hash-structure-stl.md)|Definiuje funkcję członkowską, która zwraca wartość, która jest jednoznacznie określana `thread::id`przez. Funkcja członkowska definiuje funkcję [mieszania](../standard-library/hash-class.md) , która jest odpowiednia do mapowania wartości typu `thread::id` na rozkład wartości indeksu.|

### <a name="public-functions"></a>Funkcje publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Jednoznacznie identyfikuje bieżący wątek wykonania.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje wątek wywołujący.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blokuje wątek wywołujący co najmniej do określonego czasu.|
|[swap](../standard-library/thread-functions.md#swap)|Wymienia Stany dwóch obiektów **wątku** .|
|[yield](../standard-library/thread-functions.md#yield)|Sygnalizuje systemowi operacyjnemu Uruchamianie innych wątków, nawet jeśli bieżący wątek będzie normalnie nadal działać.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator > = — operator](../standard-library/thread-operators.md#op_gt_eq)|Określa, czy `thread::id` jeden obiekt jest większy lub równy drugiemu.|
|[operator > operatora](../standard-library/thread-operators.md#op_gt)|Określa, czy `thread::id` jeden obiekt jest większy niż inny.|
|[operator < = — operator](../standard-library/thread-operators.md#op_lt_eq)|Określa, czy `thread::id` jeden obiekt jest mniejszy lub równy drugiemu.|
|[operator < operatora](../standard-library/thread-operators.md#op_lt)|Określa, czy `thread::id` jeden obiekt jest mniejszy niż inny.|
|[operator! = — operator](../standard-library/thread-operators.md#op_neq)|Porównuje `thread::id` dwa obiekty pod kątem nierówności.|
|[operator = = — operator](../standard-library/thread-operators.md#op_eq_eq)|Porównuje `thread::id` dwa obiekty pod kątem równości.|
|[operator < operatora <](../standard-library/thread-operators.md#op_lt_lt)|Wstawia tekstową reprezentację `thread::id` obiektu do strumienia.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
