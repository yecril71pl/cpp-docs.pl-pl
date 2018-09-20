---
title: _InterlockedAddLargeStatistic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6698a58ec2a5363700f7751565f1dde8e25c2bcf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415983"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft Specific**

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)