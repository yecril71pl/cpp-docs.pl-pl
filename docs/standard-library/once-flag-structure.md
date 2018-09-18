---
title: once_flag, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104338"
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
