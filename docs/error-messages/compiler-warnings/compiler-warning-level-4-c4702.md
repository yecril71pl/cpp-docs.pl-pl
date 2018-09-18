---
title: Kompilator ostrzeżenie (poziom 4) C4702 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4702
dev_langs:
- C++
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d15072099c6329eced8ab9dd9c78f8f48c31fe7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057142"
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