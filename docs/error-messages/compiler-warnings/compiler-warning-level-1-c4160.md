---
title: Kompilator ostrzeżenie (poziom 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391845"
---
# <a name="compiler-warning-level-1-c4160"></a>Kompilator ostrzeżenie (poziom 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (POP, Point,...): nie znaleziono poprzednio włożonego identyfikatora "*identyfikator*"

## <a name="remarks"></a>Uwagi

Pragma instrukcji w kodzie źródłowym próbuje pop identyfikator, który nie został wypchnięty. Aby uniknąć tego ostrzeżenia, upewnij się, prawidłowo przypisany identyfikator są zdjęte ze stosu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4160 i pokazuje, jak go naprawić:

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```