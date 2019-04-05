---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 6f9d599a8d7668c6c8a37846275e8338002589d1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033417"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Specyficzne dla firmy Microsoft**

Wykonuje dodawanie blokowane, w której pierwszy argument operacji jest wartość 64-bitową.

## <a name="syntax"></a>Składnia

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>Parametry

*Składnik dodawania*<br/>
[out w] Wskaźnik do pierwszego operandu do operacji dodawania. Wartość wskazywana jest zastępowany przez wynik dodawania.

*Wartość*<br/>
[in] Drugi operand; wartość do dodania pierwszego operandu.

## <a name="return-value"></a>Wartość zwracana

Wartość drugiego operandu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzne nie jest atomic, ponieważ jest stosowana jako dwa osobne instrukcje zablokowane. Niepodzielne odczytu 64-bitowych, występujący w innym wątku podczas wykonywania tego wewnętrznej może spowodować niespójne wartości odczytywany.

Ta funkcja działa jako czynnik blokujący odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [_readwritebarrier —](../intrinsics/readwritebarrier.md).

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)