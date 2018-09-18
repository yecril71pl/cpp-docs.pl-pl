---
title: Błąd kompilatora C2914 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2914
dev_langs:
- C++
helpviewer_keywords:
- C2914
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fddc7d479e743162a43a96a80b8d362678bf51f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027794"
---
# <a name="compiler-error-c2914"></a>Błąd kompilatora C2914

'Identyfikator': nie można wywnioskować argumentów typu jako argumentu funkcji jest niejednoznaczny

Kompilator nie może określić, które przeciążone funkcje, aby użyć argumentu generyczny lub szablonu.

Poniższy przykład spowoduje wygenerowanie C2914:

```
// C2914.cpp
// compile with: /c
void f(int);
void f(double);
template<class T> void g(void (*) (T));
void h() { g(f); }   // C2914
// try the following line instead
// void h() { g<int>(f); }
```

C2914 może również wystąpić, gdy za pomocą typów ogólnych.  Poniższy przykład spowoduje wygenerowanie C2914:

```
// C2914b.cpp
// compile with: /clr /c
void f(int);
void f(double);

template<class T>
void gf(void (*) (T));

void h() { gf(f);}   // C2914
// try the following line instead
void h() { gf<int>(f); }
```