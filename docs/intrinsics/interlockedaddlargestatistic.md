---
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: de8c5b7dfd2462dddcb98324ebacc44c8148d85e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222089"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft Specific**

Wykonuje blokadę, w której pierwszy operand jest wartością 64-bitową.

## <a name="syntax"></a>Składnia

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>Parametry

*Składnik dodawania*\
[in. out] Wskaźnik do pierwszego operandu operacji dodawania. Wartość wskazywana jest zastępowana przez wynik dodania.

*Wartościami*\
podczas Drugi operand; wartość do dodania do pierwszego operandu.

## <a name="return-value"></a>Wartość zwracana

Wartość drugiego operandu.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_InterlockedAddLargeStatistic` Wewnętrzna nie jest niepodzielna, ponieważ jest zaimplementowana jako dwie oddzielne, zablokowane instrukcje. Niepodzielna 64-bitowa odczyt, która występuje w innym wątku podczas wykonywania wewnętrznego, może spowodować odczytanie niespójnej wartości.

`_InterlockedAddLargeStatistic`zachowuje się jako bariera odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
