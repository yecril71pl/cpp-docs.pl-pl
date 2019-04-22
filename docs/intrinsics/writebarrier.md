---
title: _WriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: d2db648c9f41bd4f773f5bf152f31cf990a75c8e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025774"
---
# <a name="writebarrier"></a>_WriteBarrier

**Microsoft Specific**

Ogranicza optymalizacje kompilatora, które można zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są przestarzałe i nie powinna być używana. Do komunikacji między wątku, użyj mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md), które są określone w [ C++ biblioteki standardowej](../standard-library/cpp-standard-library-reference.md). W przypadku dostępu do sprzętu, użyj [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora wraz z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.

## <a name="syntax"></a>Składnia

```
void _WriteBarrier(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`_WriteBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które mogą usuwać lub zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)