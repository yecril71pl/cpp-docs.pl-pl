---
title: Kompilator ostrzeżenie (poziom 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 96ae3a0742db5e3a5006f031ce62beb281c38ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395251"
---
# <a name="compiler-warning-level-4-c4702"></a>Kompilator ostrzeżenie (poziom 4) C4702

nieosiągalny kod

To ostrzeżenie jest wynikiem pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: nieosiągalnego kodu. Gdy kompilator (zaplecza) wykryje nieosiągalny kod, wygeneruje C4702, ostrzeżenie poziom 4.

Kod, który jest prawidłowy w wersjach Visual Studio .NET 2003 i Visual Studio .NET, Visual c++ usuwanie nieosiągalnego kodu lub zapewnić, że każdy kod źródłowy jest dostępny za pomocą niektórych przepływem wykonania.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4702.

```
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>Przykład

Podczas kompilowania za pomocą **/GX**, **opcja/ehc**, **/ehsc**, lub **/EHac** i za pomocą funkcji extern C, kod może stać się niedostępne ponieważ extern C funkcje są zakłada się, że nie zgłosi wyjątku, dlatego blok catch nie jest osiągalny.  Jeśli uważasz, że to ostrzeżenie jest nieprawidłowa, ponieważ funkcja może zgłosić, skompilować z **/eha** lub **/EHS**, w zależności od wyjątku.

Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4702.

```
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