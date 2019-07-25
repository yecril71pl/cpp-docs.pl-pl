---
title: once_flag — Struktura
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455206"
---
# <a name="onceflag-structure"></a>once_flag — Struktura

Reprezentuje **strukturę** , która jest używana z funkcją szablonu [call_once](../standard-library/mutex-functions.md#call_once) , aby upewnić się, że kod inicjalizacji jest wywoływany tylko raz, nawet w obecności wielu wątków wykonania.

## <a name="syntax"></a>Składnia

Struktura once_flag {constexpr once_flag () noexcept;};

## <a name="remarks"></a>Uwagi

Struktura ma tylko domyślny Konstruktor.  `once_flag`

Obiekty typu `once_flag` można tworzyć, ale nie mogą być kopiowane.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
