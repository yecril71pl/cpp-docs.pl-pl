---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: fcad9c1b5ec20a7a10afc40884ece8ae8abec184
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076681"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

Zawiera nagłówek standardowej biblioteki C \<Signal. h > i dodaje skojarzone nazwy do przestrzeni nazw `std`. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w przestrzeni nazw `std`.

## <a name="syntax"></a>Składnia

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>Przestrzeń nazw i makra

```cpp
namespace std {
    using sig_atomic_t = see below;

    extern using signal-handler = void(int);
}

#define SIG_DFL
#define SIG_ERR
#define SIG_IGN
#define SIGABRT
#define SIGFPE
#define SIGILL
#define SIGINT
#define SIGSEGV
#define SIGTERM
```

## <a name="functions"></a>Funkcje

```cpp
signal-handler* signal(int sig, signal-handler* func);
int raise(int sig);
```

## <a name="see-also"></a>Zobacz też

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
Omówienie biblioteki standardowej\ [ C++ ](../standard-library/cpp-standard-library-overview.md)
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
