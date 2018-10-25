---
title: fp_contract | Dokumentacja firmy Microsoft
ms.custom: ''
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
ms.workload:
- cplusplus
ms.openlocfilehash: 95f23fa132a263970047a480ccde37382b6d03de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052167"
---
# <a name="fpcontract"></a>fp_contract

Określa, czy zmiennoprzecinkowych zmniejszenia odbywa się. Zmniejszenie zmiennoprzecinkowej jest instrukcji takich jak FMA (topionej-mnożenie-Dodawanie), który łączy dwie oddzielne operacje zmiennoprzecinkowe w pojedynczej instrukcji. Użyj tych instrukcji może wpływać na precyzję zmiennoprzecinkową, ponieważ zamiast zaokrąglając miejsce po zakończeniu każdej operacji, procesor może zaokrąglać tylko jeden raz po zarówno operacji.

## <a name="syntax"></a>Składnia

> **#pragma fp_contract (** { **na** | **poza** } **)**

## <a name="remarks"></a>Uwagi

Domyślnie **fp_contract** jest **na**. To informuje kompilator, aby można było użyć instrukcji zmiennoprzecinkowych zmniejszenia, gdzie to możliwe. Ustaw **fp_contract** do **poza** zachować pojedynczych instrukcji zmiennoprzecinkowych.

Aby uzyskać więcej informacji na temat zachowanie liczb zmiennopozycyjnych, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../build/reference/fp-specify-floating-point-behavior.md).

Inne zmiennoprzecinkowych pragm, obejmują:

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>Przykład

Kod generowany na podstawie tego przykładu nie używa instrukcję zespolone mnożenie Dodawanie, nawet wtedy, gdy jest ona dostępna na procesor docelowy. Jeśli komentarz wystąpi poza `#pragma fp_contract (off)`, wygenerowany kod może używać instrukcję zespolone mnożenie Dodawanie, jeśli jest ona dostępna.

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
