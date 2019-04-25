---
title: Błąd kompilatora C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303518"
---
# <a name="compiler-error-c2396"></a>Błąd kompilatora C2396

"your_type::operator'type": CLR lub WinRT konwersja zdefiniowana przez użytkownika functionnot prawidłowe. Należy konwertować z albo konwertować na: T ^', t ^ % ", t ^ &", gdzie T = "your_type"

Funkcja konwersji w Windows Runtime lub typ zarządzany nie miał co najmniej jeden parametr, którego typ jest taki sam jak typ zawierający funkcję konwersji.

Poniższy przykład generuje C2396 i pokazuje, jak go naprawić:

```
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```