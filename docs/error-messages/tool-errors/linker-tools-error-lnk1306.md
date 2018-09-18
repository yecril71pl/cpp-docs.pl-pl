---
title: Błąd narzędzi konsolidatora LNK1306 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc007a4a594c8593d7820365377f1c811b1e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050570"
---
# <a name="linker-tools-error-lnk1306"></a>Błąd narzędzi konsolidatora LNK1306

> Funkcja punktu wejścia biblioteki DLL nie może być zarządzany; skompilować Native

`DllMain` Nie można skompilować do MSIL; muszą być skompilowane na natywny.

Aby rozwiązać ten problem

- Skompiluj plik, który zawiera punkt wejścia bez **/CLR**.

- Umieść punkt wejścia w `#pragma unmanaged` sekcji.

Aby uzyskać więcej informacji, zobacz:

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md)

- [Inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md)

- [Zachowanie biblioteki wykonawczej DLL i Visual C++](../../build/run-time-library-behavior.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK1306.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

Aby rozwiązać ten problem, nie należy używać opcji/CLR Aby skompilować ten plik, lub użyj `#pragma` dyrektywy, należy umieścić w niezarządzanych sekcji definicji punktu wejścia, jak pokazano w poniższym przykładzie:

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
