---
title: fenv_access | Microsoft Docs
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eeb138a8b2598c209005031a3ccd3104fead48dc
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466335"
---
# <a name="fenvaccess"></a>fenv_access
Wyłącza (**na**) lub włącza (**poza**) optymalizacje, które można zmienić środowisko zmiennoprzecinkowych Flaga testy i zmiany trybu.

## <a name="syntax"></a>Składnia

> **#pragma fenv_access (** { **na** | **poza** } **)**  

## <a name="remarks"></a>Uwagi

Domyślnie **fenv_access** jest **poza**. Jeśli kompilator można założyć, że Twój kod dostępu lub nie manipulowania zmiennoprzecinkowych środowiska, a następnie można wykonywać wiele optymalizacje kodu zmiennoprzecinkowego. Ustaw **fenv_access** do **na** poinformować kompilator, że Twój kod uzyskuje dostęp do środowiska zmiennoprzecinkowych, aby przetestować flagi stanu, wyjątki, lub można ustawić flagi trybu kontroli. Kompilator wyłącza Optymalizacje te tak, aby kodu mogą uzyskiwać dostęp do środowiska zmiennoprzecinkowych spójne. 

Aby uzyskać więcej informacji na temat zachowanie liczb zmiennopozycyjnych, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../build/reference/fp-specify-floating-point-behavior.md).

Rodzaje optymalizacje, które podlegają **fenv_access** są:

- Globalne eliminacja wspólnych podwyrażeń

- Kod ruchu

- Składania stałej

Inne zmiennoprzecinkowych pragm, obejmują:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Przykłady

W tym przykładzie **fenv_access** do **na** do ustawienia rejestru sterowania zmiennoprzecinkowego dla 24-bitowa precyzja:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-003
```

Jeśli komentarz wystąpi poza `#pragma fenv_access (on)` z poprzedniego przykładu, należy pamiętać, że dane wyjściowe inny, ponieważ kompilator wykonuje oceny kompilacji, która nie używa trybu kontroli.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-002
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
