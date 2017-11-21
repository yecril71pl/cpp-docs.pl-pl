---
title: "Błąd krytyczny C1509 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1509
dev_langs: C++
helpviewer_keywords: C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d3fc7a7be867a7137dab4155984cf1844b661ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1509"></a>Błąd krytyczny C1509
ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "function". Uprość funkcję  
  
 Kod przekracza limit wewnętrzny stanów obsługi wyjątków (Zjednoczone 32 768).  
  
 Najczęstszą przyczyną jest, że funkcja zawiera wyrażenie złożone zmienne klasy użytkownika oraz operatorów arytmetycznych.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Przypisywanie typowych użyto do zmiennych tymczasowych uprościć wyrażenia.  
  
2.  Podziel funkcji na mniejsze funkcji.