---
title: Błąd kompilatora C3848
ms.date: 11/04/2016
f1_keywords:
- C3848
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
ms.openlocfilehash: 1d738311ada14999a5345a4e2394631254dda00a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381003"
---
# <a name="compiler-error-c3848"></a>Błąd kompilatora C3848

Wyrażenie typu "type" spowoduje utratę niektórych kwalifikatorów const-volatile w celu wywołania "function"

Zmienna przy użyciu określonego typu const-volatile może wywołać tylko elementu członkowskiego funkcje zdefiniowane przy użyciu tej samej lub większej kwalifikacji const-volatile.

Poniższe przykłady generują C3848:

```
// C3848.cpp
void glbFunc1()
{
}

typedef void (* pFunc1)();

struct S3
{
   operator pFunc1() // const
   {
      return &glbFunc1;
   }
};

int main()
{
   const S3 s3;
   s3();   // C3848, uncomment const qualifier
}
```