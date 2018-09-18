---
title: Błąd kompilatora C3848 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3848
dev_langs:
- C++
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81af73813f1f9c6c388ec6946ef9131cad413747
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069589"
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