---
title: Kompilator ostrzeżenie (poziom 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 2f97be4e1aaa5143df685cb95935d350e6f02534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161085"
---
# <a name="compiler-warning-level-1-c4537"></a>Kompilator ostrzeżenie (poziom 1) C4537

> "*obiektu*": "*operator*" zastosowany do typu innego niż UDT

## <a name="remarks"></a>Uwagi

Odwołanie został przekazany, gdy Oczekiwano obiektu (typ zdefiniowany przez użytkownika). Odwołanie nie jest obiektem, ale kodem wbudowanego asemblera nie będzie mógł wprowadzić rozróżnienia. Kompilator generuje kod tak, jakby *obiektu* zostały wystąpienia.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4537 i pokazuje, jak go naprawić:

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```