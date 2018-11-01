---
title: Kompilator ostrzeżenie (poziom 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: adf233673c4b654927aa9488565adf6ceef5d3e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501195"
---
# <a name="compiler-warning-level-3-c4792"></a>Kompilator ostrzeżenie (poziom 3) C4792

funkcji "function" zadeklarowana za pomocą sysimport i odwołania z kodu natywnego; Zaimportuj bibliotekę wymaganą do połączenia

Funkcji natywnej, który został zaimportowany do programu z DllImport została wywołana z niezarządzanej funkcji. W związku z tym należy połączyć Importuj biblioteki dla biblioteki DLL.

To ostrzeżenie nie można rozpoznać w kodzie lub przez zmianę sposobu kompilacji. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może wyłączyć to ostrzeżenie.

Poniższy przykład spowoduje wygenerowanie C4792:

```
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```