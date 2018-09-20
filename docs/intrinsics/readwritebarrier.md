---
title: _Readwritebarrier — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d9b970453e33aa12590f935689361d239025af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440371"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Microsoft Specific**

Ogranicza optymalizacje kompilatora, które można zmieniać kolejność dostępów do pamięci poprzez punkt wywołania.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są przestarzałe i nie powinna być używana. Do komunikacji między wątku, użyj mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md), które są określone w [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md). W przypadku dostępu do sprzętu, użyj [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora wraz z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.

## <a name="syntax"></a>Składnia

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`_ReadWriteBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które mogą usuwać lub zmieniać kolejność dostępów do pamięci poprzez punkt wywołania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)