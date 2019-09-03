---
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 8bbcecf95daeef6ea2d40877d37e0eb6b7f3a0e8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217095"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Microsoft Specific**

Ogranicza optymalizacje kompilatora, które mogą zmienić kolejność operacji dostępu do pamięci w punkcie wywołania.

> [!CAUTION]
> Elementy wewnętrzne `_WriteBarrier`,ii `_ReadWriteBarrier` makrosąprzestarzałeiniepowinnybyćużywane.`MemoryBarrier` `_ReadBarrier` W przypadku komunikacji między wątkami należy używać mechanizmów takich jak [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::\<Atom T >](../standard-library/atomic.md) , które są zdefiniowane w [ C++ standardowej bibliotece](../standard-library/cpp-standard-library-reference.md). Aby uzyskać dostęp do sprzętu, użyj opcji kompilatora [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) wraz ze słowem kluczowym [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Składnia

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_ReadBarrier` Wewnętrzna ogranicza optymalizacje kompilatora, które mogą usuwać lub zmienić kolejność operacji dostępu do pamięci w punkcie wywołania.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
