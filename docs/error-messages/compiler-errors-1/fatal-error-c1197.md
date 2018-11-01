---
title: Błąd krytyczny C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604155"
---
# <a name="fatal-error-c1197"></a>Błąd krytyczny C1197

Nie można odwołać "mscorlib.dll_1", ponieważ program istnieje już odwołanie do "mscorlib.dll_2"

Kompilator jest dopasowany do wersji środowiska uruchomieniowego języka wspólnego.  Jednak podjęto próbę odwołania wersję pliku środowiska uruchomieniowego języka wspólnego z poprzedniej wersji.

Aby rozwiązać ten problem, odwoływać się tylko pliki z wersji środowiska uruchomieniowego języka wspólnego dostarczanej z wersją programu Visual C++ są kompilowania za pomocą.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```