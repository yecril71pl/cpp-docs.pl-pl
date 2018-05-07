---
title: Błąd krytyczny C1509 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1509"></a>Błąd krytyczny C1509
ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "function". Uprość funkcję  
  
 Kod przekracza limit wewnętrzny stanów obsługi wyjątków (Zjednoczone 32 768).  
  
 Najczęstszą przyczyną jest, że funkcja zawiera wyrażenie złożone zmienne klasy użytkownika oraz operatorów arytmetycznych.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Przypisywanie typowych użyto do zmiennych tymczasowych uprościć wyrażenia.  
  
2.  Podziel funkcji na mniejsze funkcji.