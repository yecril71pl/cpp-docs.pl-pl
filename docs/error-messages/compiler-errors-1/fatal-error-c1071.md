---
title: Błąd krytyczny C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747413"
---
# <a name="fatal-error-c1071"></a>Błąd krytyczny C1071

znaleziono nieoczekiwany koniec pliku w komentarzu

Kompilator osiągnął koniec pliku podczas skanowania komentarza.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Brak terminatora komentarza (*/).

1. Brak znaku nowego wiersza po komentarzu w ostatnim wierszu pliku źródłowego.

Poniższy przykład generuje C1071:

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
