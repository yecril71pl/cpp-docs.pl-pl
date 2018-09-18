---
title: Błąd kompilatora C3482 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9921c25575888ab2db1c092f9325002d1becb921
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053378"
---
# <a name="compiler-error-c3482"></a>Błąd kompilatora C3482

"this" należy używać tylko jako przechwyt lambdy w obrębie funkcji niestatycznego elementu członkowskiego

Nie można przekazać `this` do listy przechwytywania wyrażenia lambda, które są zadeklarowane w statycznej metody lub funkcją globalną.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Konwertuj funkcji otaczającej metody niestatyczna, lub

- Usuń `this` wskaźnika z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3482:

```
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)