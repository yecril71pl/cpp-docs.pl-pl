---
title: Błąd kompilatora C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438102"
---
# <a name="compiler-error-c2396"></a>Błąd kompilatora C2396

"your_type::operator'type'': CLR lub WinRT functionnot konwersja zdefiniowana przez użytkownika prawidłowe. Należy konwertować z albo konwertować na: t ^', t ^ % ", t ^ &", gdzie T = "your_type"

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