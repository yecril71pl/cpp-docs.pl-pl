---
title: Błąd krytyczny C1071 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4487de60148e1da7668bc44c996c5dfb955a9d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033007"
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