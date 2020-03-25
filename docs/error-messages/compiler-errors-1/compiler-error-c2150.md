---
title: Błąd kompilatora C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 57c21f7ee9435220a9ca0b50bb85567506b6ad3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207223"
---
# <a name="compiler-error-c2150"></a>Błąd kompilatora C2150

> "*Identyfikator*": pole bitowe musi mieć typ "int", "ze znakiem int" lub "unsigned int"

Typ podstawowy dla pola bitowego musi być `int`, `signed int`lub `unsigned int`.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak można napotkać C2150 oraz jak można go naprawić:

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```
