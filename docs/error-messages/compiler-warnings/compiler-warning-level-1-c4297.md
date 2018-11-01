---
title: Kompilator ostrzeżenie (poziom 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 07dd6c65498ddd0d377ec3e0fbc7b44e52bec96b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540260"
---
# <a name="compiler-warning-level-1-c4297"></a>Kompilator ostrzeżenie (poziom 1) C4297

'Funkcja': Funkcja przyjmuje się, że nie zgłasza wyjątku, ale nie

Deklaracja funkcji zawiera (być może niejawną) `noexcept` specyfikator, pusta `throw` specyfikator wyjątek lub [__declspec(nothrow)](../../cpp/nothrow-cpp.md) atrybutu, jak i definicja zawiera jeden lub więcej [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) instrukcji. Aby rozwiązać C4297, nie należy próbować zgłaszanie wyjątków w funkcjach, które są zadeklarowane `__declspec(nothrow)`, `noexcept(true)` lub `throw()`. Możesz też usunąć `noexcept`, `throw()`, lub `__declspec(nothrow)` specyfikacji.

Domyślnie, kompilator generuje niejawne `noexcept(true)` specyfikatory dla zdefiniowanych przez użytkownika destruktorów i funkcje program wycofujący przydzielenia i generowane przez kompilator specjalnych funkcji Członkowskich. To jest zgodny z normą ISO C ++ 11, standard. Aby uniknąć generowania specyfikatory niejawny modyfikator noexcept i przywrócić kompilatorowi charakteryzują się niestandardowym działaniem programu Visual Studio 2013, należy użyć **/Zc:implicitNoexcept-** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/Zc: implicitnoexcept (niejawne specyfikatory wyjątków)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Aby uzyskać więcej informacji dotyczących specyfikacji wyjątków, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md). Zobacz też [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) instrukcje dotyczące sposobu modyfikowania wyjątek w zachowaniu obsługi w czasie kompilacji.

To ostrzeżenie zostanie również wygenerowany dla __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) funkcje oznaczone extern "C", nawet jeśli leżą one funkcje języka C++.

Poniższy przykład spowoduje wygenerowanie C4297:

```
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```