---
title: Błąd kompilatora C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603414"
---
# <a name="compiler-error-c2220"></a>Błąd kompilatora C2220

Ostrzeżenie potraktowano jako błąd - nie plik wygenerowanego obiektu

[/WX](../../build/reference/compiler-option-warning-level.md) nakazuje kompilatorowi na traktowanie wszystkich ostrzeżeń jako błędy. Ponieważ wystąpił błąd, żaden obiekt lub plik wykonywalny został wygenerowany.

Ten błąd pojawia się wtedy kiedy **/WX** jest ustawiona flaga i występuje ostrzeżenie podczas kompilacji. Aby naprawić ten błąd, należy wyeliminować każde ostrzeżenie w projekcie.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Aby rozwiązać problem, użyj jednej z następujących technik

- Naprawianie problemów, które powodują ostrzeżenia w projekcie.

- Skompiluj na niższym poziomie ostrzeżenia — na przykład użyć **/W3** zamiast **/W4**.

- Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może wyłączyć lub blokować szczególne ostrzeżenie.

- Nie używaj **/WX** do skompilowania.