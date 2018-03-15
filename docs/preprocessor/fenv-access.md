---
title: fenv_access | Microsoft Docs
ms.custom: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e19b4b3f1fd71d61609648f587dee9aac31e6f6
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="fenvaccess"></a>fenv_access

Wyłącza (**na**) lub włącza (**poza*) funkcje optymalizacji, które można zmienić zmiennoprzecinkowe środowiska flagę testy i zmiany trybu.

## <a name="syntax"></a>Składnia

> **#pragma fenv_access (** { **na** | **poza** } **)**  

## <a name="remarks"></a>Uwagi

Domyślnie **fenv_access** jest **poza**. Jeśli kompilator można założyć, że kod dostępu lub nie manipulowania zmiennoprzecinkowe środowiska, a następnie mogą wykonywać wiele optymalizacji liczb zmiennoprzecinkowych kodu. Ustaw **fenv_access** do **na** do informuje kompilator, że kod uzyskuje dostęp do środowiska liczb zmiennoprzecinkowych Aby sprawdzić stan flagi, wyjątki, lub można ustawić flagi trybu kontroli. Kompilator wyłącza te optymalizacje, dzięki czemu kod dostęp spójnie zmiennoprzecinkowe środowiska. 

Aby uzyskać więcej informacji dotyczących zachowania zmiennoprzecinkowego, zobacz [/fp (określenie zachowania Floating-Point)](../build/reference/fp-specify-floating-point-behavior.md).

Rodzaje funkcje optymalizacji, które podlegają **fenv_access** są:

- Globalne eliminacja wspólnych podwyrażeń

- Kod ruchu

- Składania stałej

Inne zmiennoprzecinkowych pragm obejmują:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Przykłady

W tym przykładzie **fenv_access** do **na** można ustawić Zarejestruj kontrolki liczb zmiennoprzecinkowych w 24-bitowa precyzja:

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

Jeśli możesz przekształcić w komentarz `#pragma fenv_access (on)` od poprzedniej próbki, należy pamiętać, że dane wyjściowe różnych ponieważ kompilator jest oceny kompilacji, która nie używa trybu formantu.

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
