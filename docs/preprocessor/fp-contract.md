---
title: fp_contract, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 833d8e7f4b8c9da18901610e52afed619468c5c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218562"
---
# <a name="fp_contract-pragma"></a>fp_contract, pragma

Określa, czy ma miejsce zamówienie zmiennoprzecinkowe. Umowka zmiennoprzecinkowa jest instrukcją, taką jak FMA (-mnożyć-Add), która łączy dwie oddzielne operacje zmiennoprzecinkowe w jedną instrukcję. Użycie tych instrukcji może wpłynąć na precyzję zmiennoprzecinkową, ponieważ zamiast zaokrąglania po każdej operacji, procesor może zaokrąglić tylko raz po obu operacjach.

## <a name="syntax"></a>Składnia

> **#pragma fp_contract (** { **on** | **off** } **)**

## <a name="remarks"></a>Uwagi

Domyślnie **fp_contract** jest **włączone**. Oznacza to, że kompilator będzie używać instrukcji kontraktu zmiennoprzecinkowego, jeśli jest to możliwe. Ustaw opcję **fp_contract** na **off** , aby zachować poszczególne instrukcje zmiennoprzecinkowe.

Aby uzyskać więcej informacji o zachowaniu liczb zmiennoprzecinkowych, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](../build/reference/fp-specify-floating-point-behavior.md).

Inne pragmy zmiennoprzecinkowe obejmują:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Przykład

Kod wygenerowany na podstawie tego przykładu nie używa instrukcji "pomnożyć-", nawet jeśli jest ona dostępna na docelowym procesorze. W przypadku dodania komentarza `#pragma fp_contract (off)`do wygenerowanego kodu może zostać wykorzystana instrukcja "podzielna", jeśli jest dostępna.

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

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
