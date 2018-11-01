---
title: Kompilator ostrzeżenie (poziom 1) C4906
ms.date: 11/04/2016
f1_keywords:
- C4906
helpviewer_keywords:
- C4906
ms.assetid: 05318e74-799b-412a-9dce-f02b8161d762
ms.openlocfilehash: a62b10ca96dc9c27e57eafdcc87cf0d5e0605b4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444749"
---
# <a name="compiler-warning-level-1-c4906"></a>Kompilator ostrzeżenie (poziom 1) C4906

literał ciągu rzutowany na 'LPWSTR'

Kompilator wykrył niebezpieczne rzutowania. Rzutowanie pomyślnie, ale należy użyć procedury konwersji.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4906:

```
// C4906.cpp
// compile with: /W1
#pragma warning(default : 4906)
#include <windows.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
    LPWSTR x = (LPWSTR)"1234";   // C4906

    // try the following lines instead
    // char y[128];
    // size_t numberOfCharConverted = 0;
    // errcode err = 0;
    // err = wcstombs_s(&numberOfCharConverted , &y[0], 128,
    //                  L"12345", 4);
    // if (err != 0)
    // {
    //     printf_s("wcstombs_s failed!");
    //     return -1;
    // }
    // printf_s("%s\n", y);

    return 0;
}
```