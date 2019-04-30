---
title: Kompilator ostrzeżenie (poziom 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 067d1aef41280f4d14fe799e4f4ee26a9f1b9f5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401023"
---
# <a name="compiler-warning-level-4-c4239"></a>Kompilator ostrzeżenie (poziom 4) C4239

użyto niestandardowego rozszerzenia: "token": konwersja z 'typ' do 'typ'

Ta konwersja typu nie jest dozwolona przez C++ standard, ale dozwolone jest tutaj jako rozszerzenie. To ostrzeżenie jest zawsze następuje co najmniej jeden wiersz wyjaśnienie opisujące reguły języka naruszana.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4239.

```
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>Przykład

Konwersja z typu całkowitego na typ wyliczeniowy nie jest ściśle dozwolona.

Poniższy przykład spowoduje wygenerowanie C4239.

```
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```