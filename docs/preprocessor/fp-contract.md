---
title: fp_contract | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c9b6287b71e077a7d91c60d2062b9f7243d103
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="fpcontract"></a>fp_contract

Określa, czy zmiennoprzecinkowe zmniejszenia ma miejsce. Zmiennoprzecinkowe zmniejszenia jest instrukcji, takie jak FMA (topionej-mnożenia — Dodaj), łączącą dwa osobne operacje zmiennoprzecinkowe w jednej instrukcji. Użyj tych instrukcji może mieć wpływ na dokładność liczb zmiennoprzecinkowych, ponieważ zamiast zaokrąglania po zakończeniu każdej operacji, procesor może zaokrąglona tylko raz po operacjami.

## <a name="syntax"></a>Składnia

> **#pragma fp_contract (** { **na** | **poza** } **)**  

## <a name="remarks"></a>Uwagi  

Domyślnie **fp_contract** jest **na**. Ta wartość informuje kompilator, aby używał instrukcji zmiennoprzecinkowych zmniejszenia, jeśli jest to możliwe. Ustaw **fp_contract** do **poza** w celu zachowania poszczególnych instrukcji zmiennoprzecinkowych.

Aby uzyskać więcej informacji dotyczących zachowania zmiennoprzecinkowego, zobacz [/fp (określenie zachowania Floating-Point)](../build/reference/fp-specify-floating-point-behavior.md).

Inne zmiennoprzecinkowych pragm obejmują:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Przykład

Kod wygenerowany od tego przykładu nie używa instrukcję zespolone mnożenia — Dodaj nawet wtedy, gdy jest ona dostępna na procesor docelowy. Jeśli możesz przekształcić w komentarz `#pragma fp_contract (off)`, wygenerowany kod może używać instrukcję zespolone mnożenia dodawania, jeśli jest dostępna.  
  
```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
