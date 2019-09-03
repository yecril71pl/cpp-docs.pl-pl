---
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 7819477edb8d4e6b18a1213a73ba67065ea7ff57
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219136"
---
# <a name="__writemsr"></a>__writemsr

**Microsoft Specific**

Generuje instrukcję Write do specyficznego dla modelu`wrmsr`rejestru ().

## <a name="syntax"></a>Składnia

```C
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

### <a name="parameters"></a>Parametry

*Zarejestrować*\
podczas Rejestr specyficzny dla modelu.

*Wartościami*\
podczas Wartość do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta funkcja może być używana tylko w trybie jądra, a ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
