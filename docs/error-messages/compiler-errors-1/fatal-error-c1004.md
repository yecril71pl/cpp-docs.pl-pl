---
title: Błąd krytyczny C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 13fb8963b33569facf62ccedfe9ce8b7bbbbfdc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428122"
---
# <a name="fatal-error-c1004"></a>Błąd krytyczny C1004

Nieoczekiwany koniec pliku

Kompilator osiągnięto koniec pliku źródłowego bez rozwiązywania konstrukcję. Kod może brakować jedną z następujących elementów:

- Zamykający nawias klamrowy

- Nawias zamykający

- Zamykania komentarza znacznika (* /)

- Średnikami

Aby rozwiązać ten problem, sprawdź, czy następujące czynności:

- Dysk domyślny ma za mało miejsca na pliki tymczasowe, które wymagają o dwa razy więcej miejsca, co plik źródłowy.

- `#if` Dyrektywę, który daje w wyniku wartość false nie ma zamykający `#endif` dyrektywy.

- Plik źródłowy nie może kończyć powrotu karetki i wysuwu wiersza.

Poniższy przykład spowoduje wygenerowanie C1004:

```
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Możliwe rozwiązanie:

```
// C1004b.cpp
#if TEST
#endif

int main() {}
```