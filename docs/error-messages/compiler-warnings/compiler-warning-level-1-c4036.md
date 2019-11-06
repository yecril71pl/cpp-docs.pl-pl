---
title: Ostrzeżenie kompilatora (poziom 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 858cf089d3f681438a221115c8758c38a5cf8d9a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626265"
---
# <a name="compiler-warning-level-1-c4036"></a>Ostrzeżenie kompilatora (poziom 1) C4036

nienazwane "typ" jako rzeczywisty parametr

Nie podano nazwy typu dla struktury, Unii, wyliczenia lub klasy używanej jako rzeczywisty parametr. Jeśli używasz [/zg](../../build/reference/zg-generate-function-prototypes.md) , aby generować prototypy funkcji, kompilator wystawia to ostrzeżenie i komentarze do parametru formalnego w wygenerowanym prototypie.

Określ nazwę typu, aby usunąć to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4036.

```c
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```