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
ms.openlocfilehash: 0056d54844e9396d517fd44c3649f1bc9605829b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700560"
---
# <a name="ltfuturegt-enums"></a>&lt;przyszłe&gt; Typy wyliczeniowe

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[launch](#launch)|

## <a name="future_errc"></a>  future_errc — wyliczenie

Dostarcza symbolicznych nazw dla wszystkich błędów, które są zgłaszane przez [future_error](../standard-library/future-error-class.md) klasy.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status"></a>  future_status — wyliczenie

Dostarcza nazw symbolicznych dla przyczyn, które może zwracać funkcja Przekroczono limit czasu oczekiwania.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch"></a>  Launch — wyliczenie

Reprezentuje typ maski bitów, który opisuje możliwe tryby funkcji szablonu [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Zobacz także

[\<future>](../standard-library/future.md)<br/>
