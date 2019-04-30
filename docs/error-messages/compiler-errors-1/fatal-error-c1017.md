---
title: Błąd krytyczny C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: e2309b93be65b049c35abf96572e144a0a518007
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383181"
---
# <a name="fatal-error-c1017"></a>Błąd krytyczny C1017

Nieprawidłowa liczba całkowita stałego wyrażenia

Wyrażenie w `#if` dyrektywy nie istnieje lub nie zostało obliczone do stałej.

Stałe zdefiniowane przy użyciu `#define` musi zawierać wartości, które dają stała liczba całkowita, jeśli są one używane w `#if`, `#elif`, lub `#else` dyrektywy.

Poniższy przykład spowoduje wygenerowanie C1017:

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Możliwe rozwiązanie:

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Ponieważ `CONSTANT_NAME` daje w wyniku ciągu i nie jest liczbą całkowitą, `#if` dyrektywa generuje błąd krytyczny C1017.

W innych przypadkach preprocesora ocenia undefined, stała wartość zero. Może to spowodować niezamierzone skutki, jak pokazano w następującym przykładzie. `YES` jest niezdefiniowana, więc osiągnie wartość zero. Wyrażenie `#if` `CONSTANT_NAME` daje w wyniku wartość false i kod, który ma być używany na `YES` jest usuwana przez preprocesor. `NO` jest również niezdefiniowane (zero), więc `#elif` `CONSTANT_NAME==NO` zwraca wartość true (`0 == 0`), powodując preprocesora opuścić ten kod w `#elif` część instrukcji — dokładnie przeciwieństwo to oczekiwane zachowanie.

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Aby zobaczyć dokładnie, jak kompilator obsługuje dyrektywy preprocesora, użyj [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), lub [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).