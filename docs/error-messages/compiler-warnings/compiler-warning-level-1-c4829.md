---
title: Ostrzeżenie kompilatora (poziom 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: e8765f206d099f808ab261fbbde19273e46b5c90
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051245"
---
# <a name="compiler-warning-level-1-c4829"></a>Ostrzeżenie kompilatora (poziom 1) C4829

Prawdopodobnie nieprawidłowe parametry dla funkcji main. Rozważmy "intmain (platform:: Array\<platform:: String ^ > ^ argv)"

Niektóre funkcje, takie jak Main, nie mogą przyjmować parametrów typu odwołania. Gdy kompilacja zakończy się powodzeniem, ostateczny obraz prawdopodobnie nie zostanie uruchomiony.

Poniższy przykład generuje C4829:

```cpp
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```