---
title: Instrukcja o wartości Null (C)
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
ms.openlocfilehash: 4fdfa2283e40856ccaffd55daacb697b1344134b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343419"
---
# <a name="null-statement-c"></a>Instrukcja o wartości Null (C)

"Instrukcja o wartości null" jest instrukcję, zawierającą tylko średnika; może się pojawić, wszędzie tam, gdzie jest oczekiwany instrukcję. Nic się nie dzieje, gdy jest wykonywana instrukcja o wartości null. Poprawny sposób code instrukcja o wartości null jest:

## <a name="syntax"></a>Składnia

> **;**

## <a name="remarks"></a>Uwagi

Instrukcje, takie jak **czy**, **dla**, **Jeśli**, i `while` wymagają, że instrukcji wykonywalnej są wyświetlane jako treść instrukcji. Instrukcja o wartości null spełnia wymagania składni w przypadkach, które nie są treść instrukcji merytorycznych.

Podobnie jak w przypadku innych instrukcji C, może zawierać etykiety przed instrukcja o wartości null. Oznaczenie elementu, który jest nie instrukcję, takich jak zamykającego nawiasu klamrowego instrukcji złożonej, można oznaczyć instrukcja o wartości null i wstaw go bezpośrednio przed element, aby uzyskać ten sam efekt.

Ten przykład ilustruje instrukcja o wartości null:

```C
for ( i = 0; i < 10; line[i++] = 0 )
     ;
```

W tym przykładzie wyrażenie pętli **dla** instrukcji `line[i++] = 0` inicjuje 10 pierwszych elementów `line` na 0. Treść instrukcji jest instrukcja o wartości null, ponieważ nie dalsze instrukcje są niezbędne.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
