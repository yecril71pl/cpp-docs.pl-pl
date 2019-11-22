---
title: fenv_access, pragma
description: Opisuje użycie i efekty dyrektywy pragma fenv_access. Dyrektywa fenv_access kontroluje dostęp do środowiska zmiennoprzecinkowego w czasie wykonywania.
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305857"
---
# <a name="fenv_access-pragma"></a>fenv_access, pragma

Wyłącza (**włączone**) lub włącza (**wyłączone**) optymalizacje, które mogą zmienić testy flagi środowiska zmiennoprzecinkowego i zmiany trybu.

## <a name="syntax"></a>Składnia

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>Uwagi

Domyślnie **fenv_access** jest **wyłączone**. Kompilator zakłada, że kod nie ma dostępu ani nie manipuluje środowiskiem zmiennoprzecinkowym. Jeśli dostęp do środowiska nie jest wymagany, kompilator może wykonać więcej czynności, aby zoptymalizować kod zmiennoprzecinkowy.

Włącz **fenv_access** , jeśli kod sprawdza flagi stanu zmiennoprzecinkowego, wyjątki lub ustawia flagi trybu kontroli. Kompilator wyłącza optymalizacje zmiennoprzecinkowe, dzięki czemu kod może stale uzyskiwać dostęp do środowiska zmiennoprzecinkowego.

Opcja wiersza polecenia [/FP: Strict] automatycznie włącza **fenv_access**. Aby uzyskać więcej informacji na temat tego i innych zachowań zmiennoprzecinkowych, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](../build/reference/fp-specify-floating-point-behavior.md).

Istnieją ograniczenia dotyczące sposobów używania dyrektywy pragma **fenv_access** w połączeniu z innymi ustawieniami zmiennoprzecinkowymi:

- Nie można włączyć **fenv_access** , chyba że są włączone precyzyjne semantyke. Precyzyjne semantyki można włączyć za pomocą dyrektywy pragma [float_control](float-control.md) lub za pomocą [/FP: precyzyjne](../build/reference/fp-specify-floating-point-behavior.md) lub [/FP: ścisłych](../build/reference/fp-specify-floating-point-behavior.md) opcji kompilatora. Kompilator domyślnie **/FP: precyzyjne** , jeśli nie określono żadnej innej opcji wiersza polecenia zmiennoprzecinkowego.

- Nie można użyć **float_control** , aby wyłączyć precyzyjne semantykę, gdy jest ustawiona wartość **fenv_access (włączona)** .

Rodzaje optymalizacji, które podlegają **fenv_access** są następujące:

- Eliminacja globalnego wspólnego podwyrażenia

- Ruch kodu

- Stałe łamanie

Inne pragmy zmiennoprzecinkowe obejmują:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Przykłady

Ten przykład ustawia **fenv_access** na **włączone** , aby ustawić rejestr kontroli zmiennoprzecinkowej dla dokładności 24-bitowej:

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

W przypadku dodawania komentarza do `#pragma fenv_access (on)` z poprzedniego przykładu dane wyjściowe są inne. Jest to spowodowane tym, że kompilator wykonuje ocenę czasu kompilacji, która nie używa trybu kontroli.

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
