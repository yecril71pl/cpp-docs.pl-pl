---
title: '&lt;CTime&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ctime>
- std::<ctime>
helpviewer_keywords:
- ctime header
ms.assetid: c1f7d4a4-4bfe-4e35-92cb-f63dbd3c39a8
ms.openlocfilehash: 2b3f31ba48ca831b2d2d8cd460b60549c4debe83
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076624"
---
# <a name="ltctimegt"></a>&lt;CTime&gt;

Zawiera nagłówek standardowej biblioteki C \<Time. h > i dodaje skojarzone nazwy do przestrzeni nazw `std`.

## <a name="syntax"></a>Składnia

```cpp
#include <ctime>
```

## <a name="remarks"></a>Uwagi

Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w przestrzeni nazw `std`.

## <a name="constants"></a>Stałe

```cpp
#define NULL
#define CLOCKS_PER_SEC
#define TIME_UTC

namespace std {
    using size_t = see below;
    using clock_t = see below ;
    using time_t = see below ;
}
```

## <a name="structures"></a>Struktury

```cpp
struct timespec;
struct tm;
```

## <a name="functions"></a>Funkcje

```cpp
clock_t clock();
double difftime(time_t time1, time_t time0);
time_t mktime(struct tm* timeptr);
time_t time(time_t* timer);
int timespec_get(timespec* ts, int base);
char* asctime(const struct tm* timeptr);
char* ctime(const time_t* timer);
struct tm* gmtime(const time_t* timer);
struct tm* localtime(const time_t* timer);
size_t strftime(char* s, size_t maxsize, const char* format, const struct tm* timeptr);
```

## <a name="see-also"></a>Zobacz też

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
Omówienie biblioteki standardowej\ [ C++ ](../standard-library/cpp-standard-library-overview.md)
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
