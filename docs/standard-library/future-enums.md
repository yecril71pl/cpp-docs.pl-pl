---
title: '&lt;przyszłe&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: a32f777842b3c14a5c6f15d9c1c3b534bc4ffad8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
