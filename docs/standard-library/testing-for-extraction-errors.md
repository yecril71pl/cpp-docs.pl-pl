---
title: Testing for Extraction Errors | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 088cc150513d593aff5d4250c899eb3712c5fe39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="testing-for-extraction-errors"></a>Testing for Extraction Errors
Dane wyjściowe funkcji przetwarzania błędu, omówione w [błąd przetwarzania funkcje](../standard-library/output-file-stream-member-functions.md), dotyczą strumienie. Testowanie pod kątem błędów podczas wyodrębniania jest ważne. Należy wziąć pod uwagę tej instrukcji:  
  
```  
cin>> n;  
```  
  
 Jeśli `n` jest całkowita, wartość większą niż 32 767 (maksymalna dozwolona wartość lub MAX_INT) ustawia strumień `fail` bit i `cin` obiektu staje się bezużyteczny. Wszystkie kolejne ekstrakcje powoduje natychmiastowe powrotu bez wartości przechowywane.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

