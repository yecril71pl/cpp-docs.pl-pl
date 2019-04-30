---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 8a7829252cebb726363c67c990a94d08b0d6467a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389219"
---
# <a name="floatcontrol"></a>float_control

Określa zachowanie liczb zmiennopozycyjnych dla funkcji.

## <a name="syntax"></a>Składnia

> **#pragma float_control** [ **(** [ *wartość* **,** *ustawienie* [ **, wypychania** ]] | [ **wypychania** | **pop** ] **)** ]

## <a name="options"></a>Opcje

*wartość*, *ustawienie* [, **wypychania**]<br/>
Określa zachowanie liczb zmiennopozycyjnych. *wartość* może być **dokładne**, **strict**, lub **z wyjątkiem**. Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../build/reference/fp-specify-floating-point-behavior.md). *Ustawienie* albo można **na** lub **poza**.

Jeśli *wartość* jest **strict**, ustawienia dla obu **strict** i **z wyjątkiem** są określone przez *ustawienie* . **z wyjątkiem** można ustawić tylko **na** podczas **dokładne** lub **strict** jest również ustawiona na **na**.

Jeśli opcjonalny **wypychania** token zostanie dodany, bieżące ustawienie *wartość* zostanie przypisany wewnętrznym stosie kompilatora.

**push**<br/>
Wypychanie bieżącej **float_control** ustawienie na wewnętrznym stosie kompilatora

**POP**<br/>
Usuwa **float_control** ustawienie z góry wewnętrznego stosu kompilatora i sprawia, że nowe **float_control** ustawienie.

## <a name="remarks"></a>Uwagi

Nie można użyć **float_control** włączyć **dokładne** wyłączone, gdy **z wyjątkiem** znajduje się na. Podobnie **dokładne** nie może być wyłączone podczas [fenv_access](../preprocessor/fenv-access.md) znajduje się na. Aby przejść z ograniczeniami modelu do szybkiego modelu przy użyciu **float_control** pragma, użyj następującego kodu:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Można przejść od szybkie modelu do modelu ściśle z **float_control** pragma, użyj następującego kodu:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Jeśli nie określono opcji, **float_control** nie ma wpływu.

Inne zmiennoprzecinkowych pragm, obejmują:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak catch przepełnienie zmiennoprzecinkowej wyjątek za pomocą pragmy **float_control**.

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
