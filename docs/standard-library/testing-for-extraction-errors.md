---
title: Testing for Extraction Errors
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: db551a21fd33665d83b11373f040be158406d492
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453662"
---
# <a name="testing-for-extraction-errors"></a>Testing for Extraction Errors

Funkcje przetwarzania błędów wyjścia, omówione w [funkcjach przetwarzania błędów](../standard-library/output-file-stream-member-functions.md), mają zastosowanie do strumieni wejściowych. Testowanie błędów podczas wyodrębniania jest ważne. Należy wziąć pod uwagę następujące instrukcje:

```cpp
cin>> n;
```

Jeśli `n` jest to liczba całkowita ze znakiem, wartość większa niż 32 767 (maksymalna dopuszczalna wartość lub MAX_INT) ustawia `fail` bit strumienia, a `cin` obiekt stanie się bezużyteczny. Wszystkie kolejne operacje wyodrębniania powodują natychmiastowe zwrócenie bez żadnej wartości.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)
