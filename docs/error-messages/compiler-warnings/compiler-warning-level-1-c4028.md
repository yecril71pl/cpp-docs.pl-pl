---
title: Kompilator ostrzeżenie (poziom 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397370"
---
# <a name="compiler-warning-level-1-c4028"></a>Kompilator ostrzeżenie (poziom 1) C4028

Parametr formalny "number" różni się od deklaracji

Typ parametrów formalnych nie zgadza się z odpowiednim parametrem w deklaracji. Typ w oryginalnej deklaracji jest używany.

To ostrzeżenie jest prawidłowy tylko dla kodu źródłowego C.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4028.

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```