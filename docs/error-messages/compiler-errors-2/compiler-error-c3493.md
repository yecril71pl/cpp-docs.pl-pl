---
title: Błąd kompilatora C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: ece70a99477b018f6d7a935911f475e4fb4397cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548008"
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