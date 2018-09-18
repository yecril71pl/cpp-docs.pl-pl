---
title: Kompilator ostrzeżenie (poziom 1) C4835 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70492be13d312c5d167990cfa0b6c0d741e1055f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080106"
---
# <a name="compiler-warning-level-1-c4835"></a>Kompilator ostrzeżenie (poziom 1) C4835

'Zmienna': Inicjator dla eksportowanych danych nie będzie działać, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta

Podczas uzyskiwania dostępu do danych między składników zarządzanych, zaleca się nie używać natywnego języka C++ importu i eksportu mechanizmów. Zamiast tego należy zadeklarować członkom danych wewnątrz typu zarządzanego i odwoływać się do metadanych z `#using` w kliencie. Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4835.

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Przykład

Poniższy przykład używa składnika utworzone w poprzednim przykładzie, pokazujący, że wartości zmiennych nie jest zgodne z oczekiwaniami.

```
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```