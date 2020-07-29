---
title: Błąd kompilatora C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: f217e0b94e27c0f85879e80b3ae887cb4f76f486
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216365"
---
# <a name="compiler-error-c2084"></a>Błąd kompilatora C2084

Funkcja "*Function*" ma już treść

Funkcja została już zdefiniowana.

Przed Visual Studio 2002,

- Kompilator akceptuje wiele specjalizacji szablonów, które zostały rozpoznane do tego samego rzeczywistego typu, chociaż dodatkowe definicje nigdy nie będą dostępne. Kompilator wykrywa teraz te wiele definicji.

- **`__int32`** i **`int`** były traktowane jako oddzielne typy. Kompilator traktuje teraz **`__int32`** jako synonim dla **`int`** . Oznacza to, że kompilator wykrywa wiele definicji, jeśli funkcja jest przeciążona w obu **`__int32`** i występuje **`int`** błąd.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Aby naprawić ten błąd, Usuń zduplikowaną definicję:

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
