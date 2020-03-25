---
title: Ostrzeżenie kompilatora (poziom 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 31deba2f421b461ba56d13810b5064b353a0e602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175678"
---
# <a name="compiler-warning-level-1-c4297"></a>Ostrzeżenie kompilatora (poziom 1) C4297

"Function": funkcja założono, że nie zgłosić wyjątku, ale

Deklaracja funkcji zawiera specyfikator `noexcept` (prawdopodobnie niejawny), pusty specyfikator wyjątku `throw` lub atrybut [__declspec (nothrow)](../../cpp/nothrow-cpp.md) , a definicja zawiera jedną lub więcej instrukcji [throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Aby rozwiązać C4297, nie należy próbować zgłaszać wyjątków w funkcjach, które są zadeklarowane `__declspec(nothrow)`, `noexcept(true)` lub `throw()`. Alternatywnie Usuń specyfikację `noexcept`, `throw()`lub `__declspec(nothrow)`.

Domyślnie kompilator generuje niejawne specyfikatory `noexcept(true)` dla destruktorów zdefiniowanych przez użytkownika i funkcji dealokacji oraz specjalnych funkcji składowych generowanych przez kompilator. Jest to zgodne ze standardem ISO C++ 11. Aby zapobiec generowaniu niejawnych specyfikatorów noexcept i przywrócić kompilator do niestandardowych zachowań Visual Studio 2013, użyj opcji **/Zc: implicitNoexcept-** Compiler. Aby uzyskać więcej informacji, zobacz [/Zc: implicitNoexcept (niejawne specyfikatory wyjątków)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Aby uzyskać więcej informacji dotyczących specyfikacji wyjątków, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md). Ponadto zobacz [/EH (model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md) , aby uzyskać informacje na temat modyfikowania zachowania obsługi wyjątków w czasie kompilacji.

To ostrzeżenie jest również generowane dla funkcji __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) oznaczonych jako extern "C", nawet jeśli C++ są one funkcjami.

Poniższy przykład generuje C4297:

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
