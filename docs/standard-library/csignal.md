---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: 298aa14c4e41f1473cac72fc79aa3e180dfe183f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243558"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

Dołącza nagłówek biblioteki standardowe C \<sygnale > i dodaje skojarzone nazwy `std` przestrzeni nazw. Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane przez zewnętrzne powiązanie w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.


## <a name="syntax"></a>Składnia

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>Makra i Namespace

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

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
