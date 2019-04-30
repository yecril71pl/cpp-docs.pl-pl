---
title: Instrukcja wyrażeń
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2973c3e0a1cd59edfc7ef1e771454b780da23cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400607"
---
# <a name="expression-statement"></a>Instrukcja wyrażeń

Instrukcje wyrażeń spowodować wyrażeń, które ma zostać obliczone. Żaden transfer formantu lub iteracji odbywa się w wyniku instrukcji wyrażenia.

Składnia instrukcji wyrażenia jest po prostu

## <a name="syntax"></a>Składnia

```
[expression ] ;
```

## <a name="remarks"></a>Uwagi

Wszystkie wyrażenia w instrukcji wyrażenia są obliczane i wszystkie efekty uboczne są zakończone przed wykonaniem następnej instrukcji. Najbardziej typowe instrukcje wyrażeń są przypisania i wywołania funkcji.  Ponieważ wyrażenie jest opcjonalne, samodzielnie średnik jest uznawany za instrukcji wyrażenia empty, nazywane [null](../cpp/null-statement.md) instrukcji.

## <a name="see-also"></a>Zobacz także

[Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)