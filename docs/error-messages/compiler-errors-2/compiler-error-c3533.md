---
title: Błąd kompilatora C3533 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6201f59e3ccefaa920f79f9b9889bd187fb2e0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042562"
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

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)
