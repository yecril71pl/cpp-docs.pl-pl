---
title: Błąd krytyczny C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756971"
---
# <a name="fatal-error-c1004"></a>Błąd krytyczny C1004

znaleziono nieoczekiwany koniec pliku

Kompilator osiągnął koniec pliku źródłowego bez rozpoznawania konstrukcji. Kod może nie zawierać jednego z następujących elementów:

- Zamykający nawias klamrowy

- Nawias zamykający

- Znacznik zamykającego komentarza (*/)

- Średnik

Aby rozwiązać ten problem, sprawdź następujące kwestie:

- Na domyślnym dysku nie ma wystarczającej ilości miejsca na pliki tymczasowe, które wymagają około dwukrotnie większej ilości miejsca jako pliku źródłowego.

- Dyrektywa `#if`, która ma wartość false, nie ma dyrektywy zamykającej `#endif`.

- Plik źródłowy nie kończy się znakiem powrotu karetki i wysuwu wiersza.

Poniższy przykład generuje C1004:

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Możliwe rozwiązanie:

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
