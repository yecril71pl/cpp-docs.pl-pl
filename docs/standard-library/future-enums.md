---
title: '&lt;przyszłe&gt; wyliczenia'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0f1064fdf434560c3130d1254512470cc5bc1ee0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370695"
---
# <a name="ltfuturegt-enums"></a>&lt;przyszłe&gt; wyliczenia

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Uruchom](#launch)|

## <a name="future_errc-enumeration"></a><a name="future_errc"></a>Future_errc Wyliczenie

Dostarcza symboliczne nazwy dla wszystkich błędów, które są zgłaszane przez [future_error](../standard-library/future-error-class.md) klasy.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a>Future_status Wyliczenie

Dostarcza nazwy symboliczne z powodów, dla których funkcja czasowego oczekiwania może powrócić.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a>uruchom Wyliczenie

Reprezentuje typ maski bitowej opisujący możliwe tryby dla funkcji szablonu [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Zobacz też

[\<przyszłych>](../standard-library/future.md)
