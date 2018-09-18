---
title: Błąd kompilatora C3803 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3803
dev_langs:
- C++
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a841dbaae4142e92d8e0987b0618285e4f71f60
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075869"
---
# <a name="compiler-error-c3803"></a>Błąd kompilatora C3803

"właściwość": właściwość ma typ, który nie jest zgodny z jednym z jego metody dostępu "akcesor"

Typ właściwości zdefiniowane za pomocą [właściwość](../../cpp/property-cpp.md) jest niezgodny z typem zwracanym dla jednej z jej funkcji dostępu.

Poniższy przykład spowoduje wygenerowanie C3803:

```
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```