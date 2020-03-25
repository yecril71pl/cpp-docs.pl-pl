---
title: Błąd kompilatora C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206031"
---
# <a name="compiler-error-c2383"></a>Błąd kompilatora C2383

"*symbol*": argumenty domyślne nie są dozwolone w tym symbolu

C++ Kompilator nie zezwala na argumenty domyślne dla wskaźników do funkcji.

Ten kod został zaakceptowany przez C++ kompilator firmy Microsoft w wersjach przed programem Visual Studio 2005, ale teraz zawiera błąd. Dla kodu, który działa we wszystkich wersjach wizualizacji C++, nie należy przypisywać wartości domyślnej do argumentu wskaźnika do funkcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2383 i zawiera możliwe rozwiązanie:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
