---
title: '&lt;clocale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <clocale>
helpviewer_keywords:
- clocale header
ms.assetid: 5bde3e01-cf67-4f1f-a383-447ec814d00e
ms.openlocfilehash: 60d15795328de567a8ba626f5344b2fb08e57aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459353"
---
# <a name="ltclocalegt"></a>&lt;clocale&gt;

Zawiera standardowe ustawienia regionalne nagłówka \<biblioteki języka C. h > i dodaje skojarzone nazwy `std` do przestrzeni nazw.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<CLocale >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są `std` deklarowane w przestrzeni nazw.

## <a name="constants"></a>Stałe

```cpp
#define NULL see below
#define LC_ALL see below
#define LC_COLLATE see below
#define LC_CTYPE see below
#define LC_MONETARY see below
#define LC_NUMERIC see below
#define LC_TIME see below
```

## <a name="structures"></a>Struktury

```cpp
struct lconv;
```

## <a name="functions"></a>Funkcje

```cpp
char* setlocale(int category, const char* locale);
lconv* localeconv();
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
