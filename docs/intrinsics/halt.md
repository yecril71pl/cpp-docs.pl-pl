---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222148"
---
# <a name="__halt"></a>__halt

**Microsoft Specific**

Zatrzymuje mikroprocesor do momentu włączenia włączonego przerwania, przerwania niemaskowanego (NMI) lub zresetowania.

## <a name="syntax"></a>Składnia

```C
void __halt( void );
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__halt`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `HLT` z instrukcją Machine i jest dostępna tylko w trybie jądra. `__halt` Aby uzyskać więcej informacji, Wyszukaj dokument "Podręcznik Intel Architecture Developer, Tom 2: Odwołanie do zestawu instrukcji "w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
