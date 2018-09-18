---
title: Błąd kompilatora C2220 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4179b396e732ceeea20aeb9428d841a357a6d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051324"
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