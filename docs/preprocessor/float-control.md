---
title: float_control, pragma
description: Opisuje użycie i efekty dyrektywy pragma float_control. Dyrektywa float_control steruje stanem precyzyjnej semantycznej semantyki i semantyki wyjątku w czasie wykonywania.
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 02a8e8d80616623693fff04aca02355c505b4c3b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041929"
---
# <a name="float_control-pragma"></a>float_control, pragma

Określa zachowanie zmiennoprzecinkowe dla funkcji.

## <a name="syntax"></a>Składnia

> **#pragma float_control**\
> **#pragma float_control (precyzyjne,** { **on**  |  **off** } [ **, push** ] **)**\
> **#pragma float_control (z wyjątkiem,** { **on**  |  **off** } [ **, push** ] **)**\
> **#pragma float_control (** { **push**  |  **pop** } **)**

## <a name="options"></a>Opcje

**precyzyjne**, **on**  |  **wyłączone**, **wypychane**\
Określa, czy włączyć (**włączona**) Czy wyłączyć (**wyłączyć**) precyzyjne semantykę liczb zmiennoprzecinkowych. Aby uzyskać informacje o różnicach w opcji kompilatora **/FP: precyzyjne** , zobacz sekcję Uwagi. Opcjonalny token **wypychania** wypycha bieżące ustawienie dla **float_control** na wewnętrznym stosie kompilatora.

**z wyjątkiem**, **on**  |  **off**, **push**\
Określa, czy włączyć (**Włącz**) Czy wyłączyć (**off**) semantykę wyjątku zmiennoprzecinkowego. Opcjonalny token **wypychania** wypycha bieżące ustawienie dla **float_control** na wewnętrznym stosie kompilatora.

**chyba że** można ustawić tylko **na wartość włączone** , tylko wtedy, gdy jest również ustawiony **na wartość** **włączone**.

**wydajności**\
Wypchnięcie bieżące ustawienie **float_control** do wewnętrznego stosu kompilatora.

**skakując**\
Usuwa ustawienie **float_control** z góry wewnętrznego stosu kompilatora i sprawia, że nowe **float_control** ustawienie.

## <a name="remarks"></a>Uwagi

**Float_control** pragma nie ma takiego samego zachowania jak opcja kompilatora [/FP](../build/reference/fp-specify-floating-point-behavior.md) . **Float_control** pragma reguluje tylko część zachowania zmiennoprzecinkowego. Aby ponownie utworzyć opcje kompilatora **/FP** , należy je połączyć z [fp_contract](../preprocessor/fp-contract.md) i [fenv_access](../preprocessor/fenv-access.md) pragma. W poniższej tabeli przedstawiono równoważne ustawienia dyrektywy pragma dla każdej opcji kompilatora:

| Opcja | float_control (precyzyjne \* ) | float_control (z wyjątkiem, \* ) | fp_contract ( \* ) | fenv_access ( \* ) |
|-|-|-|-|-|
| /FP: Strict             | on  | on  | wyłączone | on  |
| /FP: Precyzyjna            | on  | wyłączone | on  | wyłączone |
| /FP: szybka               | wyłączone | wyłączone | on  | wyłączone |

Innymi słowy, może być konieczne użycie kilku pragm w połączeniu do emulowania opcji wiersza polecenia **/FP: Fast**, **/FP: precyzyjne**i **/FP: Strict** .

Istnieją ograniczenia dotyczące sposobów używania **float_control** i **fenv_accessj** pragma zmiennoprzecinkowa w połączeniu:

- Opcji **float_control** można używać tylko do ustawiania **z wyjątkiem** **włączony, jeśli precyzyjne** semantyki są włączone. Precyzyjne semantyki można włączyć za pomocą dyrektywy pragma **float_control** lub za pomocą **/FP: precyzyjne** lub **/FP: ścisłych** opcji kompilatora.

- Nie można użyć **float_control** , aby wyłączyć **precyzyjne** , gdy semantyka wyjątków jest włączona, niezależnie od tego, czy jest to **float_control** pragma czy **/FP: z wyjątkiem** kompilatora.

- Nie można włączyć **fenv_access** , jeśli nie są włączone precyzyjne semantyke, niezależnie od tego, czy jest to **float_control** pragma czy opcja kompilatora.

- Nie można użyć **float_control** , aby wyłączyć **precyzyjne** , gdy **fenv_access** jest włączona.

Ograniczenia te oznaczają kolejność niektórych pragm zmiennoprzecinkowych. Aby przejść od szybkiego modelu do modelu Strict przy użyciu pragmów, użyj następującego kodu:

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

Aby przejść z ścisłego modelu do szybkiego modelu przy użyciu dyrektywy pragma **float_control** , użyj następującego kodu:

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

Jeśli nie określono żadnych opcji, **float_control** nie ma żadnego wpływu.

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

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
