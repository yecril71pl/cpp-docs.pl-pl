---
title: Kompilator ostrzeżenie (poziom 3) C4995 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4995
dev_langs:
- C++
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5ae389fef72681c6a8b31c9790c6773535f467d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053482"
---
# <a name="compiler-warning-level-3-c4995"></a>Kompilator ostrzeżenie (poziom 3) C4995

'Funkcja': nazwa została oznaczona jako przestarzała #pragma

Kompilator napotkał funkcję oznaczoną jako zaniechana pragma [przestarzałe](../../preprocessor/deprecated-c-cpp.md). Przyszła wersja prawdopodobnie nie będzie obsługiwała tej funkcji. Możesz wyłączyć to ostrzeżenie za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma (przykład poniżej).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4995:

```
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```