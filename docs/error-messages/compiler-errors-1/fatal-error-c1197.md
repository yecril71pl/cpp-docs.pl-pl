---
title: Błąd krytyczny C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747244"
---
# <a name="fatal-error-c1197"></a>Błąd krytyczny C1197

nie można odwołać się do pliku "mscorlib. dll_1", ponieważ istnieje już odwołanie do programu "mscorlib. dll_2"

Kompilator jest zgodny z wersją środowiska uruchomieniowego języka wspólnego.  Jednak podjęto próbę odwołania się do wersji pliku środowiska uruchomieniowego języka wspólnego z poprzedniej wersji.

Aby rozwiązać ten problem, należy tylko odwoływać się do plików z wersji środowiska uruchomieniowego języka wspólnego, która została dostarczona z wersją wizualizacji C++ , która jest kompiluje.

## <a name="example"></a>Przykład

Poniższy przykład generuje C1197:

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
