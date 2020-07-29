---
title: Błąd kompilatora C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 0cb6235f1b6bc868655cc6a6ba301be1308402cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221084"
---
# <a name="compiler-error-c3386"></a>Błąd kompilatora C3386

"Type": __declspec (dllexport)/ \_ _declspec (dllimport) nie można zastosować do zarządzanego lub winrttype

`dllimport`Modyfikatory i [dllexport](../../cpp/dllexport-dllimport.md) **`__declspec`** c ' * * nie są prawidłowe w typie zarządzanym lub środowisko wykonawcze systemu Windows.

Poniższy przykład generuje C3386 i pokazuje, jak to naprawić:

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
