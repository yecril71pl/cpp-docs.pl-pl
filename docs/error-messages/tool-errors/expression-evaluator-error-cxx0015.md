---
title: Błąd CXX0015 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196069"
---
# <a name="expression-evaluator-error-cxx0015"></a>Błąd CXX0015 programu Expression Evaluator

wyrażenie jest zbyt złożone (przepełnienie stosu)

Wprowadzone wyrażenie jest zbyt złożone lub zagnieżdżone zbyt głęboko dla ilości miejsca do magazynowania dostępnego dla ewaluatora wyrażeń w języku C.

Przepełnienie występuje zwykle z powodu zbyt wielu oczekujących obliczeń.

Przemieść ponownie wyrażenie, aby można było ocenić każdy składnik wyrażenia w miarę jego napotkania, a nie trzeba czekać, aż pozostałe części wyrażenia mają zostać obliczone.

Podziel wyrażenie na wiele poleceń.

Ten błąd jest identyczny z CAN0015.
