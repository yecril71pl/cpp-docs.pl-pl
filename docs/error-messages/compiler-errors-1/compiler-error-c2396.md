---
title: Błąd kompilatora C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744839"
---
# <a name="compiler-error-c2396"></a>Błąd kompilatora C2396

"your_type:: operator'type" ": zdefiniowana przez użytkownika konwersja CLR lub WinRT functionnot prawidłowa. Należy wykonać konwersję z lub przekonwertować do: "t ^", "^%", "^ &", gdzie T = "your_type"

Funkcja konwersji w środowisko wykonawcze systemu Windows lub typie zarządzanym nie ma co najmniej jednego parametru, którego typ jest taki sam jak typ zawierający funkcję konwersji.

Poniższy przykład generuje C2396 i pokazuje, jak to naprawić:

```cpp
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
