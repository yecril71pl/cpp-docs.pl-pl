---
title: Ostrzeżenie kompilatora (poziom 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 4fe99e12c5d2dfb725e1e4aa0ac2fb0b1ccb4f28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219888"
---
# <a name="compiler-warning-level-4-c4571"></a>Ostrzeżenie kompilatora (poziom 4) C4571

Informacyjne: semantyka catch (...) zmieniła się od Visual C++ 7,1; wyjątki strukturalne (SEH) nie są już przechwytywane

C4571 jest generowany dla każdego bloku catch (...) podczas kompilowania z **/EHS**.

Podczas kompilowania z **/EHS**, blok catch (...) nie będzie przechwytywać wyjątku strukturalnego (na przykład dzielenia przez zero, wskaźnika o wartości null); blok catch (...) będzie przechwytywać tylko jawnie zgłoszone wyjątki języka C++.  Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

To ostrzeżenie jest domyślnie wyłączone.  Włącz to ostrzeżenie, aby upewnić się, że podczas kompilowania z użyciem bloków catch (...) **/EHS** nie mają być przechwytywane wyjątki strukturalne.  Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Można rozwiązać C4571 w jeden z następujących sposobów:

- Kompiluj z **/EHa** , jeśli nadal chcesz, aby bloki catch (...) przechwytywać wyjątki strukturalne.

- Nie włączaj C4571, jeśli nie chcesz, aby bloki catch (...) mogły przechwytywać wyjątki strukturalne, ale nadal chcesz używać bloków catch (...).  Nadal można przechwytywać wyjątki strukturalne przy użyciu słów kluczowych obsługujących wyjątek strukturalny (**__try**, **`__except`** i **`__finally`** ).  Należy jednak pamiętać, że skompilowane destruktory **/EHS** będą wywoływane tylko wtedy, gdy zostanie zgłoszony wyjątek języka C++, a nie w przypadku wystąpienia wyjątku SEH.

- Zamień blok catch (...) na bloki catch dla określonych wyjątków C++ i opcjonalnie Dodaj obsługę wyjątków strukturalnych wokół obsługi wyjątków C++ (**__try**, **`__except`** i **`__finally`** ).  Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) .

Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4571.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
