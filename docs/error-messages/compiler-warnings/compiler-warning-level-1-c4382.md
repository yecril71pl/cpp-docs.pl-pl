---
title: Kompilatora (poziom 1) ostrzeżenie C4382 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29afe066fb86d0dd99216a63c057046ec76de55b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704324"
---
# <a name="compiler-warning-level-1-c4382"></a>Kompilator C4382 ostrzegawcze (poziom 1)

> wyrzucanie "*typu*": typ z destruktorem __clrcall lub konstruktorem kopiującym można tylko przechwycić w/CLR: pure modułu

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Podczas kompilacji za pomocą **/CLR** (nie **/CLR: pure**), obsługa wyjątków oczekuje funkcji Członkowskich w typie natywnym za [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne przy użyciu funkcji Członkowskich `__clrcall` konwencji wywoływania nie można przechwycić w module skompilowanym z **/CLR**.

Jeśli wyjątek zostanie przechwycony w module skompilowanym z **/CLR: pure**, możesz zignorować to ostrzeżenie.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```