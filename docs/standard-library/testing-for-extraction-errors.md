---
title: Testing for Extraction Errors | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9394f387546f9b9dccf72f532148aa2b9161ce15
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="testing-for-extraction-errors"></a>Testing for Extraction Errors

Dane wyjściowe funkcji przetwarzania błędu, omówione w [błąd przetwarzania funkcje](../standard-library/output-file-stream-member-functions.md), dotyczą strumienie. Testowanie pod kątem błędów podczas wyodrębniania jest ważne. Należy wziąć pod uwagę tej instrukcji:

```cpp
cin>> n;
```

Jeśli `n` jest całkowita, wartość większą niż 32 767 (maksymalna dozwolona wartość lub MAX_INT) ustawia strumień `fail` bit i `cin` obiektu staje się bezużyteczny. Wszystkie kolejne ekstrakcje powoduje natychmiastowe powrotu bez wartości przechowywane.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
