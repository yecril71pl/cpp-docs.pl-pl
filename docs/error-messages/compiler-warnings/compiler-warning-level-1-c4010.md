---
title: Ostrzeżenie kompilatora (poziom 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 045b3f6e615e11c24caa9a088baf6ea9f6448efb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627318"
---
# <a name="compiler-warning-level-1-c4010"></a>Ostrzeżenie kompilatora (poziom 1) C4010

Komentarz jednowierszowy zawiera znak kontynuacji wiersza

Jednowierszowy komentarz, który jest wprowadzany przez//, zawiera ukośnik odwrotny (\\), który służy jako znak kontynuacji wiersza. Kompilator traktuje następny wiersz jako kontynuację i traktuje go jako komentarz.

Niektóre redaktory skierowane do składni nie wskazują wiersza następującego po znaku kontynuacji jako komentarza. Ignoruj kolorowanie składni dla wszystkich wierszy, które powodują to ostrzeżenie.

Poniższy przykład generuje C4010:

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```