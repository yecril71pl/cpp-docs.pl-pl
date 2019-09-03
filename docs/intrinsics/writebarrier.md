---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219311"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Microsoft Specific**

Ogranicza optymalizacje kompilatora, które mogą zmienić kolejność operacji dostępu do pamięci w punkcie wywołania.

> [!CAUTION]
> Elementy wewnętrzne `_WriteBarrier`,ii `_ReadWriteBarrier` makrosąprzestarzałeiniepowinnybyćużywane.`MemoryBarrier` `_ReadBarrier` W przypadku komunikacji między wątkami należy używać mechanizmów takich jak [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::\<Atom T >](../standard-library/atomic.md), które są zdefiniowane w [ C++ standardowej bibliotece](../standard-library/cpp-standard-library-reference.md). Aby uzyskać dostęp do sprzętu, użyj opcji kompilatora [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) wraz ze słowem kluczowym [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Składnia

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_WriteBarrier` Wewnętrzna ogranicza optymalizacje kompilatora, które mogą usuwać lub zmienić kolejność operacji dostępu do pamięci w punkcie wywołania.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
