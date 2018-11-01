---
title: once_flag — Struktura
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 004a5545e2eccab83b0846e2ae30b88c8431c99d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481974"
---
# <a name="onceflag-structure"></a>once_flag — Struktura

Reprezentuje **struktury** używany za pomocą funkcji szablonu [call_once —](../standard-library/mutex-functions.md#call_once) aby upewnić się, że inicjowanie kodu jest wywoływana tylko raz, nawet w obecności wielu wątków wykonania.

## <a name="syntax"></a>Składnia

once_flag — struktura {constexpr once_flag() noexcept;};

## <a name="remarks"></a>Uwagi

`once_flag` **Struktury** ma Konstruktor domyślny.

Obiekty typu `once_flag` mogą być tworzone, ale ich nie można skopiować.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
