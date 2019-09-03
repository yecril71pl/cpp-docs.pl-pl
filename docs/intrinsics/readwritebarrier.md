---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217972"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Microsoft Specific**

Ogranicza optymalizacje kompilatora, które mogą zmienić kolejność dostępu do pamięci w punkcie wywołania.

> [!CAUTION]
> Elementy wewnętrzne `_WriteBarrier`,ii `_ReadWriteBarrier` makrosąprzestarzałeiniepowinnybyćużywane.`MemoryBarrier` `_ReadBarrier` W przypadku komunikacji między wątkami należy używać mechanizmów takich jak [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::\<Atom T >](../standard-library/atomic.md), które są zdefiniowane w [ C++ standardowej bibliotece](../standard-library/cpp-standard-library-reference.md). Aby uzyskać dostęp do sprzętu, użyj opcji kompilatora [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) wraz ze słowem kluczowym [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Składnia

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_ReadWriteBarrier` Wewnętrzna ogranicza optymalizacje kompilatora, które mogą usuwać lub zmienić kolejność dostępu do pamięci w punkcie wywołania.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
