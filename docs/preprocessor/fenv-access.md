---
title: fenv_access, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218605"
---
# <a name="fenv_access-pragma"></a>fenv_access, pragma

Wyłącza (**włączone**) lub włącza (**wyłączone**) optymalizacje, które mogą zmienić testy flagi środowiska zmiennoprzecinkowego i zmiany trybu.

## <a name="syntax"></a>Składnia

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Uwagi

Domyślnie **fenv_access** jest **wyłączona**. Jeśli kompilator może założyć, że kod nie uzyskuje dostępu do środowiska zmiennoprzecinkowego lub nie manipuluje nim, może wykonać wiele optymalizacji kodu zmiennoprzecinkowego. Ustaw **fenv_access** na wartość **on** , aby informować kompilator, że kod uzyskuje dostęp do środowiska zmiennoprzecinkowego w celu testowania flag stanu, wyjątków lub ustawiania flag trybu sterowania. Kompilator wyłącza te optymalizacje, aby kod mógł spójnie uzyskiwać dostęp do środowiska zmiennoprzecinkowego.

Aby uzyskać więcej informacji o zachowaniu liczb zmiennoprzecinkowych, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](../build/reference/fp-specify-floating-point-behavior.md).

Rodzaje optymalizacji, które podlegają **fenv_access** są następujące:

- Eliminacja globalnego wspólnego podwyrażenia

- Ruch kodu

- Stałe łamanie

Inne pragmy zmiennoprzecinkowe obejmują:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Przykłady

Ten przykład ustawia **fenv_access** na **włączone** , aby ustawić rejestr kontroli zmiennoprzecinkowej dla precyzji 24-bitowej:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
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
out=9.999999776482582e-03
```

Jeśli komentarz `#pragma fenv_access (on)` pochodzi z poprzedniego przykładu, należy zauważyć, że dane wyjściowe różnią się, ponieważ kompilator wykonuje Szacowanie czasu kompilacji, które nie korzysta z trybu kontroli.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
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
out=1.000000000000000e-02
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
