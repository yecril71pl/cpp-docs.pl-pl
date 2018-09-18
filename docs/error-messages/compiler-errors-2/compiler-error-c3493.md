---
title: Błąd kompilatora C3493 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad3c46117e77d432af27321165f1e1ab93d2ef3c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045110"
---
# <a name="compiler-error-c3493"></a>Błąd kompilatora C3493

"var" nie może być niejawnie przechwycone, ponieważ nie podano żadnego domyślnego trybu przechwytywania

Przechwytywania wyrażenia lambda pusty `[]`, określa, że wyrażenie lambda nie nie zostały jawnie lub niejawnie przechwycić żadnych zmiennych.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Podaj domyślny tryb przechwytywania, lub

- Jawnie Przechwyć co najmniej jednej zmiennej.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3493, ponieważ modyfikuje zmienną zewnętrznych, ale określa pusta klauzula przechwytywania:

```
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>Przykład

Poniższy przykład jest rozpoznawana jako C3493, określając przez odwołanie jako domyślny tryb przechwytywania.

```
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)