---
title: C2129 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d151c774672b1788ca893a9812deb3e41100dc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2129"></a>C2129 błąd kompilatora
Funkcja statyczna "function" zadeklarowana ale niezdefiniowana  
  
 Do przodu odnosi się do `static` funkcji, które nigdy nie jest zdefiniowany.  
  
 A `static` funkcja musi być zdefiniowana w zakresie pliku. Jeśli funkcja jest zdefiniowany w innym pliku, może być deklarowana `extern`.