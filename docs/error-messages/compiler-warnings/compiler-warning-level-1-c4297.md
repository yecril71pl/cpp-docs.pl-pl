---
title: Kompilator ostrzeżenie (poziom 1) C4297 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f615df5933cfc93918b05758f042c8cf47aa92f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099437"
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