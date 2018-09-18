---
title: Kompilator ostrzeżenie (poziom 4) C4239 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4239
dev_langs:
- C++
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a68de05ff999e72fc02a75d5958a7e2589f8ed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032845"
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