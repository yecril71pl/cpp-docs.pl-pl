---
title: Kompilator ostrzeżenie (poziom 3) C4240 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f3c059e63bcca9bbde9e863cc17c9e240e4f78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057018"
---
# <a name="compiler-warning-level-3-c4240"></a>Kompilator ostrzeżenie (poziom 3) C4240

użyto niestandardowego rozszerzenia: dostęp do "classname" teraz zdefiniowany jako "specyfikator dostępu", poprzednio został zdefiniowany jako "specyfikatorze dostępu"

W obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nie można zmienić dostępu do klasy zagnieżdżonej. W obszarze domyślna rozszerzenia Microsoft (/Ze) można za pomocą tego ostrzeżenia.

## <a name="example"></a>Przykład

```
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```