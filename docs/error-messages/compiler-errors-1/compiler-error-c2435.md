---
title: Błąd kompilatora C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438538"
---
# <a name="compiler-error-c2435"></a>Błąd kompilatora C2435

> "*var*": dynamiczna Inicjalizacja wymaga zarządzanego CRT, nie można kompilować z/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Inicjowanie zmiennej globalnej domeny dla aplikacji wymaga CRT skompilowany przy użyciu `/clr:pure`, nie tworzy obraz możliwe do zweryfikowania.

Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```