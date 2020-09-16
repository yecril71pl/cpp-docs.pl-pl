---
title: Błąd kompilatora C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: ea2c1a3d9a10fee455d20490f0408982f47ee0a7
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684732"
---
# <a name="compiler-error-c3493"></a>Błąd kompilatora C3493

nie można przechwycić "var", ponieważ nie określono żadnego domyślnego trybu przechwytywania

Puste wyrażenie lambda przechwytuje, `[]` określa, że wyrażenie lambda nie jawnie lub niejawnie nie przechwytuje żadnych zmiennych.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Określ domyślny tryb przechwytywania lub

- Jawnie Przechwyć co najmniej jedną zmienną.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C3493, ponieważ modyfikuje zmienną zewnętrzną, ale określa pustą klauzulę przechwytywania:

```cpp
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

Poniższy przykład rozwiązuje C3493 przez określenie jako domyślny tryb przechwytywania.

```cpp
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
