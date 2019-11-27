---
title: Ostrzeżenie kompilatora (poziom 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: 84a8a8bbb08ac97fe87d63d1ea44587790f87d92
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189343"
---
# <a name="compiler-warning-level-3-c4792"></a>Ostrzeżenie kompilatora (poziom 3) C4792

Funkcja "Function" została zadeklarowana przy użyciu SysImport i przywoływana z kodu natywnego; Biblioteka importowana wymagana do konsolidacji

Funkcja natywna zaimportowana do programu z elementem DllImport została wywołana z funkcji niezarządzanej. W związku z tym należy połączyć się z biblioteką importu biblioteki DLL.

Tego ostrzeżenia nie można rozpoznać w kodzie lub poprzez zmianę sposobu kompilowania. Aby wyłączyć to ostrzeżenie, użyj dyrektywy pragma [ostrzeżenia](../../preprocessor/warning.md) .

Poniższy przykład generuje C4792:

```cpp
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