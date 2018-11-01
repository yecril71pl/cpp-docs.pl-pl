---
title: Błąd kompilatora C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: fd8909b664f739afa1ab1208be0984b8f410154d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468643"
---
# <a name="compiler-error-c3484"></a>Błąd kompilatora C3484

Oczekiwano "->" przed zwracanym typem

Należy podać `->` przed zwracanym typem wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Podaj `->` przed zwracanym typem.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3484:

```
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3484, zapewniając `->` przed zwracanym typem wyrażenia lambda:

```
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)