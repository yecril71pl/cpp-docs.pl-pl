---
title: Błąd krytyczny kompilatora zasobów RC1102 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1102
dev_langs:
- C++
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f92c7faf3c5c2d58aabba5ecf4d8d401470cfc5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Błąd krytyczny kompilatora zasobów RC1102
Błąd wewnętrzny: za dużo argumentów elementu RCPP  
  
 Zbyt wiele argumentów zostało przekazanych do preprocesora kompilatora zasobów. Zmniejsz liczbę symbole zdefiniowane przy użyciu symboli zdefiniuj (/ d) opcja, definiując je w źródle. Ten błąd może być również spowodowane określenie zbyt wiele zawiera ścieżki wyszukiwania plików przy użyciu opcji zawierają ścieżki wyszukiwania (/ i).