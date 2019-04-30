---
title: Błąd kompilatora C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 7a567e4396999f98d9e9740db0acf951c443d525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397383"
---
# <a name="compiler-error-c3533"></a>Błąd kompilatora C3533

"type": parametr nie może mieć typu zawierającego "auto"

Nie można zadeklarować parametru metody lub szablonu ze `auto` — słowo kluczowe Jeśli domyślna [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora jest aktywna.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Usuń `auto` słowo kluczowe z deklaracji parametru.

## <a name="example"></a>Przykład

Poniższy przykład daje C3533, ponieważ deklaruje parametr funkcji o `auto` słowa kluczowego i jest kompilowany za pomocą **/Zc: Auto**.

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3533 trybem C ++ 14, ponieważ deklaruje parametr szablonu, za pomocą `auto` słowa kluczowego i jest kompilowany za pomocą **/Zc: Auto**. (W języku C ++ 17, jest to prawidłowej definicji szablonu klasy z parametrem jednego szablonu bez typu, którego typ jest ustalane).

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)
