---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 1e76110c1ef0c4b98c295578189eedc99d76eeb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396629"
---
# <a name="nop"></a>__nop

**Microsoft Specific**

Generuje kod maszynowy specyficzne dla platformy, która nie wykonuje żadnej operacji.

## <a name="syntax"></a>Składnia

```
void __nop();
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="remarks"></a>Uwagi

`__nop` Funkcji jest odpowiednikiem `NOP` machine instrukcji. Aby uzyskać więcej informacji na temat x86 i x64, wyszukaj dokumentu, "Manual deweloper oprogramowania architekturze firmy Intel, wolumin 2: Instrukcja Ustaw odwołanie,"w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)
