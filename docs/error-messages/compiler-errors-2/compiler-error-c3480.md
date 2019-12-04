---
title: Błąd kompilatora C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 255fb12d587a94aac798814736f0b26770f608b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760481"
---
# <a name="compiler-error-c3480"></a>Błąd kompilatora C3480

"var": zmienna przechwytywania lambda musi pochodzić z otaczającego zakresu funkcji

Zmienna przechwytywania lambda nie jest z otaczającego zakresu funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń zmienną z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3480, ponieważ zmienna `global` nie jest z otaczającego zakresu funkcji:

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Przykład

Poniższy przykład rozwiązuje C3480 przez usunięcie zmiennej `global` z listy przechwytywania wyrażenia lambda:

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
