---
title: Ostrzeżenie kompilatora (poziom 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990649"
---
# <a name="compiler-warning-level-4-c4702"></a>Ostrzeżenie kompilatora (poziom 4) C4702

nieosiągalny kod

To ostrzeżenie jest wynikiem działania kompilatora, który został wykonany dla programu Visual Studio .NET 2003: nieosiągalny kod. Gdy kompilator (zaplecza) wykryje nieosiągalny kod, generuje C4702, ostrzeżenie poziomu 4.

W przypadku kodu, który jest prawidłowy zarówno w programie Visual Studio .NET 2003, jak i w wersji C++Visual Studio .NET, Usuń nieosiągalny kod lub zagwarantowania, że cały kod źródłowy jest dostępny dla pewnego przepływu wykonania.

## <a name="example"></a>Przykład

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

## <a name="example"></a>Przykład

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
