---
title: Testing for Extraction Errors
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: 62d9c94f366ec666acf2179803c62e4a3ccd7e6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629232"
---
# <a name="testing-for-extraction-errors"></a>Testing for Extraction Errors

Dane wyjściowe błędu przetwarzania funkcje omówione w [błąd przetwarzania funkcji](../standard-library/output-file-stream-member-functions.md), dotyczą strumienie wejściowe. Testowanie pod kątem błędów podczas wyodrębniania jest ważne. Należy wziąć pod uwagę tej instrukcji:

```cpp
cin>> n;
```

Jeśli `n` jest liczba całkowita ze znakiem, wartość większą niż 32 767 znaków (maksymalna dozwolona wartość lub MAX_INT) ustawia strumień `fail` bit i `cin` obiekt staje się bezużyteczny. Wszystkie kolejne wyodrębniania doprowadzić do bezpośredniego zwrotu bez wartości przechowywane.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
