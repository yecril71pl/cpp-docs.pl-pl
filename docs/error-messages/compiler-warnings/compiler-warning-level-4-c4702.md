---
title: Ostrzeżenie kompilatora (poziom 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: a2d1f6f4bdc20a35638274e2099c00428f4f6ddf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684290"
---
# <a name="compiler-warning-level-4-c4702"></a>Ostrzeżenie kompilatora (poziom 4) C4702

nieosiągalny kod

To ostrzeżenie jest wynikiem działania kompilatora, który został wykonany dla programu Visual Studio .NET 2003: nieosiągalny kod. Gdy kompilator (zaplecza) wykryje nieosiągalny kod, generuje C4702, ostrzeżenie poziomu 4.

W przypadku kodu, który jest prawidłowy zarówno w wersjach programu Visual Studio .NET 2003, jak i Visual Studio .NET Visual C++, Usuń nieosiągalny kod lub zagwarantowania, że cały kod źródłowy jest dostępny dla pewnego przepływu wykonania.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C4702.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

W przypadku kompilowania z **/GX**, **/EHC**, **/EHsc**lub **/EHac** i używania funkcji extern c kod może stać się nieosiągalny, ponieważ nie są zakładane funkcje extern c, w związku z czym blok catch nie jest dostępny.  Jeśli uważasz, że to ostrzeżenie jest nieprawidłowe, ponieważ funkcja może zgłosić, skompilować przy użyciu **/EHa** lub **/EHS**, w zależności od zgłoszonego wyjątku.

Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md) , aby uzyskać więcej informacji.

Poniższy przykład generuje C4702.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
