---
title: '&lt;przyszłe&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 6e228eb538a0d281dff8066390b0c6dd2e7ea4d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843850"
---
# <a name="ltfuturegt-enums"></a>&lt;przyszłe&gt; wyliczenia

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[launch](#launch)|

## <a name="future_errc"></a>  future_errc — wyliczenie

Dostarcza nazw symbolicznych wszystkie błędy, które są zgłaszane przez [future_error —](../standard-library/future-error-class.md) klasy.

future_errc klasy — {broken_promise, future_already_retrieved, promise_already_satisfied, no_state};

## <a name="future_status"></a>  future_status — wyliczenie

Dostarcza nazw symbolicznych z powodów zwracających w funkcji czasu oczekiwania.

```cpp
enum future_status{    ready,
    timeout,
 deferred};
```

## <a name="launch"></a>  Launch — wyliczenie

Reprezentuje typ maski, który opisuje możliwe tryby funkcji szablonu [async](../standard-library/future-functions.md#async).

Klasa uruchamiania {asynchroniczne, odroczone};

## <a name="see-also"></a>Zobacz także

[\<future>](../standard-library/future.md)<br/>
