---
title: Błąd kompilatora C3480 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3480
dev_langs:
- C++
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd58a8c38ee6dc5f77ef280ba3b7a546a666cd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107867"
---
# <a name="compiler-error-c3480"></a>Błąd kompilatora C3480

"var": zmienna przechwytująca lambdę musi być z otaczającego zakresu funkcji

Zmienna przechwytująca lambdę nie pochodzi z otaczającego zakresu funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń zmienną z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3480, ponieważ zmienna `global` nie pochodzi z otaczającego zakresu funkcji:

```
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3480, usuwając zmiennej `global` z listy przechwytywania wyrażenia lambda:

```
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)