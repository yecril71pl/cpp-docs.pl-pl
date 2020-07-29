---
title: once_flag — Struktura
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 55c3f90f72857a4e4cd3f9075ce5bae10e14d218
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202730"
---
# <a name="once_flag-structure"></a>once_flag — Struktura

Reprezentuje **`struct`** , który jest używany z funkcją szablonu [call_once](../standard-library/mutex-functions.md#call_once) , aby upewnić się, że kod inicjalizacji jest wywoływany tylko raz, nawet w obecności wielu wątków wykonania.

## <a name="syntax"></a>Składnia

Struktura once_flag {constexpr once_flag () noexcept;};

## <a name="remarks"></a>Uwagi

`once_flag` **`struct`** Ma tylko domyślny Konstruktor.

Obiekty typu `once_flag` można tworzyć, ale nie mogą być kopiowane.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<mutex>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
