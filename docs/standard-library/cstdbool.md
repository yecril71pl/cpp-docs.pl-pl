---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341103"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

Zawiera nagłówek \<standardowej biblioteki C stdbool. h > i dodaje skojarzone nazwy `std` do przestrzeni nazw.

> [!NOTE]
> Ponieważ nagłówek stdbool. h > definiuje makra, które są słowami C++kluczowymi, w tym nie ma żadnego wpływu. \< Nagłówek > stdbool. h jest przestarzały w programie C++ \< Nagłówek \<> cstdbool jest przestarzały w języku c++ 17 i został usunięty z wersji Standard c++ 20.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cstdbool >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są `std` deklarowane w przestrzeni nazw.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[C++Omówienie biblioteki standardowej](cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](thread-safety-in-the-cpp-standard-library.md)
