---
title: Błąd krytyczny C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 8fe6b0f3bb1253f72c97f29070ba81cdbdf80508
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166662"
---
# <a name="fatal-error-c1071"></a>Błąd krytyczny C1071

Nieoczekiwany koniec pliku w komentarzu

Kompilator osiągnięto koniec pliku podczas skanowania komentarz.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Brak komentarza terminator (* /).

1. Brak znaku nowego wiersza po komentarz w ostatnim wierszu pliku źródłowego.

Poniższy przykład spowoduje wygenerowanie C1071:

```
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```