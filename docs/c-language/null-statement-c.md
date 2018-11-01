---
title: Instrukcja o wartości Null (C)
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
ms.openlocfilehash: bee044049ed14796a97edc62bbb180ab19700564
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503055"
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

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)