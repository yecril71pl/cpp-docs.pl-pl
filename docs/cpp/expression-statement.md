---
title: Instrukcja wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f026a91846196e34f97b4d2cbcfa2c9fa749e8b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058610"
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