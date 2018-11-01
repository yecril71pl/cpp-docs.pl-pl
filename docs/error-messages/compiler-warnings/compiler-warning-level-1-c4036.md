---
title: Kompilator ostrzeżenie (poziom 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 632e88bb64568c97e937e83e177598054a954f22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609576"
---
# <a name="compiler-warning-level-1-c4036"></a>Kompilator ostrzeżenie (poziom 1) C4036

nienazwane "type" jako rzeczywisty parametr

Nazwa typu, nie jest określony dla struktury, złożenia, wyliczenia lub klasą używaną jako rzeczywisty parametr. Jeśli używasz [/Zg](../../build/reference/zg-generate-function-prototypes.md) do Generuj prototypy funkcji, kompilator generuje to ostrzeżenie i komentarze parametrów formalnych w prototypie wygenerowany.

Należy określić nazwę typu, aby rozwiązać tego ostrzeżenia.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4036.

```
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```