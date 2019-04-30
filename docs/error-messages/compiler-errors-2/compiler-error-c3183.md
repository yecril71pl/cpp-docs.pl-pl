---
title: Błąd kompilatora C3183
ms.date: 11/04/2016
f1_keywords:
- C3183
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
ms.openlocfilehash: 232e9999bc31ac3e01833e7982acfb03e9d0afaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382375"
---
# <a name="compiler-error-c3183"></a>Błąd kompilatora C3183

Nie można zdefiniować nienazwanej klasy, struktury lub związku wewnątrz zarządzanego lub WinRT, wpisz "type"

Typ, który jest osadzony w zarządzanej lub WinRT musi nosić nazwę typu.

Poniższy przykład spowoduje wygenerowanie C3183:

```
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
