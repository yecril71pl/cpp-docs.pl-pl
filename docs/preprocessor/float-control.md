---
title: float_control, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218580"
---
# <a name="float_control-pragma"></a>float_control, pragma

Określa zachowanie zmiennoprzecinkowe dla funkcji.

## <a name="syntax"></a>Składnia

> **#pragma float_control**\
> **#pragma float_control (** { **precyzyjne** | **ścisłe** | ,**z wyjątkiem** } **,** { **on** | **off** } [ **, push** ] **)** \
> **#pragma float_control (** { **push** | **pop** } **)**

## <a name="options"></a>Opcje

**precyzyjne** **ścisłe** **z wyjątkiem**, **on**off, push |  |  | \
Określa zachowanie zmiennoprzecinkowe, które może być **precyzyjne**, **ścisłe**lub **z wyjątkiem**. Aby uzyskać więcej informacji, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](../build/reference/fp-specify-floating-point-behavior.md). Ustawienie może być **włączone** lub **wyłączone**.

W przypadku opcji **Strict**ustawienia dla obu parametrów **Strict** i **except** są określone przez ustawienie **Włącz** lub **Wyłącz** . **chyba że** można ustawić tylko na wartość **włączone** , tylko wtedy, gdy jest również ustawiona wartość **włączone**.

W przypadku dodania opcjonalnego tokenu wypychania bieżące ustawienie dla **float_control** jest wypychane do wewnętrznego stosu kompilatora.

**wydajności**\
Wypchnij bieżące ustawienie **float_control** do wewnętrznego stosu kompilatora

**skakując**\
Usuwa ustawienie **float_control** z góry wewnętrznego stosu kompilatora i sprawia, że nowe ustawienie **float_control** .

## <a name="remarks"></a>Uwagi

Nie można użyć **float_control** , aby wyłączyć **precyzyjne** , gdy **z wyjątkiem** jest włączone. Podobnie, **precyzyjne** nie można wyłączyć, gdy [fenv_access](../preprocessor/fenv-access.md) jest włączone. Aby przejść z ścisłego modelu do szybkiego modelu przy użyciu dyrektywy pragma **float_control** , użyj następującego kodu:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Aby przejść od szybkiego modelu do rygorystycznego modelu z **float_control** pragma, użyj następującego kodu:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Jeśli nie określono żadnych opcji, **float_control** nie ma żadnego wpływu.

Inne pragmy zmiennoprzecinkowe obejmują:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak przechwytywać przepełnienie wyjątku zmiennoprzecinkowego za pomocą dyrektywy pragma **float_control**.

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

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
