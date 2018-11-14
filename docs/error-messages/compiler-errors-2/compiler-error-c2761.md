---
title: Błąd kompilatora C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 1236cfaf70781b6ca80db1a317a0c1b01b0f2740
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520923"
---
# <a name="compiler-error-c2761"></a>Błąd kompilatora C2761

'Funkcja': ponowna deklaracja funkcji składowej nie jest dozwolone

Nie można ponownie zadeklarować funkcji składowej. Możesz zdefiniować go, ale nie ponownie zadeklarować.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2761.

```
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

## <a name="example"></a>Przykład

Nie można zdefiniować niestatycznych elementów członkowskich klasy lub struktury.  Poniższy przykład spowoduje wygenerowanie C2761.

```
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```