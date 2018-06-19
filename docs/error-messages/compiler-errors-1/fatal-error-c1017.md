---
title: Błąd krytyczny C1017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1017
dev_langs:
- C++
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08433109a959b324621e9c837e67cf529d9f6fdb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199722"
---
# <a name="fatal-error-c1017"></a>Błąd krytyczny C1017
Nieprawidłowa liczba całkowita stałego wyrażenia  
  
 Wyrażenie w `#if` dyrektywy nie istnieje lub nie zostało obliczone do stałej.  
  
 Stałe zdefiniowane przy użyciu `#define` muszą mieć wartości, których ocena ma całkowitą wartością stałą, jeśli są używane w `#if`, `#elif`, lub `#else` dyrektywy.  
  
 Poniższy przykład generuje C1017:  
  
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
  
 Ponieważ `CONSTANT_NAME` daje w wyniku ciąg i nie jest liczbą całkowitą, `#if` dyrektywy generuje błąd krytyczny C1017.  
  
 W pozostałych przypadkach preprocesora oblicza stała undefined jako zero. Może to spowodować niezamierzone skutki, jak pokazano w poniższym przykładzie. `YES` jest niezdefiniowana, więc wynikiem jego obliczenia zero. Wyrażenie `#if` `CONSTANT_NAME` daje w wyniku wartość FAŁSZ i kod, który ma być używany dla `YES` jest usuwany przez preprocesora. `NO` jest również Niezdefiniowany (zero), więc `#elif` `CONSTANT_NAME==NO` zwraca wartość true (`0 == 0`), powoduje preprocesora pozostawić kod w `#elif` część instrukcji — dokładnie przeciwieństwem oczekiwane zachowanie.  
  
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