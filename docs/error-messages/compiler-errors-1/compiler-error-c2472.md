---
title: Błąd kompilatora C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350913"
---
# <a name="compiler-error-c2472"></a>Błąd kompilatora C2472

> "*funkcja*" nie można wygenerować w zarządzanym kodzie: "*komunikat*"; skompiluj z/CLR aby wygenerować mieszany obraz

## <a name="remarks"></a>Uwagi

Ten błąd wystąpi, jeśli typy nie są obsługiwane przez kod zarządzany używanych w ramach czystego środowiska uruchomieniowego języka wspólnego (CLR). Kompiluj przy użyciu **/CLR** Aby naprawić błąd.

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2472.

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>Zobacz także

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)
