---
title: '&lt;wątek&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 43fb79ceda6de7409e6f93797ce2f4ff213c43ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487519"
---
# <a name="ltthreadgt"></a>&lt;wątek&gt;

Dołączyć standardowy nagłówek \<wątku > w celu zdefiniowania klasy **wątku** i różne funkcje pomocnicze.

## <a name="syntax"></a>Składnia

```cpp
#include <thread>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, tego pliku nagłówkowego jest zablokowany.

`__STDCPP_THREADS__` — Makro jest zdefiniowany jako wartość różną od zera, aby wskazać, że wątki są obsługiwane przez ten nagłówek.

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Publiczne klasy

|Nazwa|Opis|
|----------|-----------------|
|[thread, klasa](../standard-library/thread-class.md)|Definiuje obiekt, który jest używany do obserwowania i zarządzania wątkiem wykonywania w aplikacji.|

### <a name="public-structures"></a>Publiczne struktury

|Nazwa|Opis|
|----------|-----------------|
|[hash, struktura (Standardowa biblioteka C++)](../standard-library/hash-structure-stl.md)|Definiuje funkcja elementu członkowskiego, która zwraca wartość, która jednoznacznie jest określana przez `thread::id`. Funkcja elementu członkowskiego zdefiniowano [skrótu](../standard-library/hash-class.md) funkcja, która jest odpowiednia do mapowania wartości typu `thread::id` do rozłożenia wartości indeksu.|

### <a name="public-functions"></a>Funkcji publicznych

|Nazwa|Opis|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Jednoznacznie identyfikuje bieżącego wątku wykonywania.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje wątek wywołujący.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blokuje wątek wywołujący, co najmniej do określonego czasu.|
|[swap](../standard-library/thread-functions.md#swap)|Zamienia dwa stany **wątku** obiektów.|
|[yield](../standard-library/thread-functions.md#yield)|Sygnały systemu operacyjnego do uruchomienia innych wątków, nawet wtedy, gdy bieżący wątek zazwyczaj będzie nadal działał.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator > = — Operator](../standard-library/thread-operators.md#op_gt_eq)|Określa, czy jeden `thread::id` obiekt jest większy niż lub równy innemu.|
|[operator > — Operator](../standard-library/thread-operators.md#op_gt)|Określa, czy jeden `thread::id` obiekt jest większy niż inny.|
|[Operator < = — Operator](../standard-library/thread-operators.md#op_lt_eq)|Określa, czy jeden `thread::id` obiekt jest mniejszy niż lub równe drugiemu.|
|[Operator < — Operator](../standard-library/thread-operators.md#op_lt)|Określa, czy jeden `thread::id` obiekt jest mniejszy niż inny.|
|[operator! = — Operator](../standard-library/thread-operators.md#op_neq)|Porównuje dwa `thread::id` obiekty pod kątem nierówności.|
|[operator == — Operator](../standard-library/thread-operators.md#op_eq_eq)|Porównuje dwa `thread::id` obiekty pod kątem równości.|
|[Operator << — Operator](../standard-library/thread-operators.md#op_lt_lt)|Wstawia tekstowa reprezentacja `thread::id` obiektu do strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
