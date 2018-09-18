---
title: Błąd kompilatora C3483 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: decc04f25689b24c560f59a71fd22a9708754352
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091689"
---
# <a name="compiler-error-c3483"></a>Błąd kompilatora C3483

"var" jest już częścią listy przechwytów lambdy

Tę samą zmienną jest przekazywane do listy przechwytywania wyrażenia lambda więcej niż jeden raz.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Z listy przechwytywania, należy usunąć wszystkie dodatkowe wystąpienia w zmiennej.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3483, ponieważ zmienna `n` pojawia się więcej niż jeden raz na liście przechwytywania wyrażenia lambda:

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)