---
title: Błąd ewaluatora wyrażeń CXX0015 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050819"
---
# <a name="expression-evaluator-error-cxx0015"></a>Błąd CXX0015 programu Expression Evaluator

wyrażenie jest zbyt złożone (przepełnienie stosu)

Wprowadzone wyrażenie jest zbyt złożonego lub zagnieżdżone zbyt głęboko ilości miejsca dostępnego na Ewaluator wyrażeń C w magazynie.

Z powodu zbyt wielu obliczeń oczekujące zwykle występuje przepełnienie.

Rozmieszczanie wyrażenie, tak aby każdy składnik wyrażenie może przyjąć, ponieważ jest ona napotkał, zamiast czekać na inne części wyrażenia, które mają być obliczane.

Podziel wyrażenia na wielu poleceń.

Ten błąd jest taka sama jak CAN0015.