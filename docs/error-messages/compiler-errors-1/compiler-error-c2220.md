---
title: Błąd kompilatora C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206664"
---
# <a name="compiler-error-c2220"></a>Błąd kompilatora C2220

Ostrzeżenie potraktowano jako błąd — nie Wygenerowano pliku obiektu

[/WX](../../build/reference/compiler-option-warning-level.md) instruuje kompilator, aby traktuje wszystkie ostrzeżenia jako błędy. Ponieważ wystąpił błąd, nie Wygenerowano obiektu ani pliku wykonywalnego.

Ten błąd pojawia się tylko wtedy, gdy flaga **/WX** jest ustawiona, a podczas kompilacji występuje ostrzeżenie. Aby naprawić ten błąd, należy wyeliminować każde ostrzeżenie w projekcie.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Aby rozwiązać ten problem, użyj jednej z następujących technik

- Rozwiąż problemy, które powodują ostrzeżenia w projekcie.

- Kompiluj z niższym poziomem ostrzeżeń — na przykład użyj **/W3** zamiast **/W4**.

- Użyj [ostrzeżenia](../../preprocessor/warning.md) pragma, aby wyłączyć lub pominąć określone ostrzeżenie.

- Nie używaj **/WX** do kompilowania.
