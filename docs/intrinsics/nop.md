---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221673"
---
# <a name="__nop"></a>__nop

**Microsoft Specific**

Generuje kod maszynowy specyficzny dla platformy, który nie wykonuje operacji.

## <a name="syntax"></a>Składnia

```C
void __nop();
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `NOP` z instrukcją maszyny. `__nop` Aby uzyskać więcej informacji na temat architektury x86 i x64, Wyszukaj dokument "Podręcznik Intel Architecture Developer, Tom 2: Odwołanie do zestawu instrukcji "w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
