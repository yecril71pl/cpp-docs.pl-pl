---
title: Kompilator ostrzeżenie (poziom 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 43c72855dbb40e93cb219e4461dbbf81d086ea79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386541"
---
# <a name="compiler-warning-level-1-c4216"></a>Kompilator ostrzeżenie (poziom 1) C4216

użyto niestandardowego rozszerzenia: float long

Traktuj domyślnych rozszerzeń firmy Microsoft (/Ze) **float long** jako **double**. Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nie jest. Użyj **double** zachować zgodność. Poniższy przykład spowoduje wygenerowanie C4216:

```
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```