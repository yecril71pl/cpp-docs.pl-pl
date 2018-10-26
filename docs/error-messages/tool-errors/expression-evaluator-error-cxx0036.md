---
title: Błąd ewaluatora wyrażeń CXX0036 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94ed846d2d4ebda2e457ee772a9f8bf081d69d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077175"
---
# <a name="expression-evaluator-error-cxx0036"></a>Błąd CXX0036 programu Expression Evaluator

Zły kontekst {...} specyfikacja

Ten komunikat może zostać wygenerowany przez dowolnego z kilku błędów w stosowaniu operator kontekstu (**{}**).

- Składnia operator kontekstu (**{}**) podano niepoprawnie.

   Składnia operator kontekstu jest następująca:

     {*funkcja*,*modułu*,*dll*}*wyrażenia*

   Określa kontekst *wyrażenie*. Operator kontekstu ma ten sam priorytet i użycia jako rzutowanie typu.

   Można pominąć końcowe przecinkami. Jeśli dowolny z *funkcja*, *modułu*, lub *dll* zawiera przecinek literału, całą nazwę należy ująć w nawiasy.

- Nazwa funkcji został wpisany niepoprawnie lub nie istnieje w określonym module lub biblioteka dołączana dynamicznie.

   Ponieważ C jest rozróżniana wielkość liter języka, *funkcja* musi być podany w dokładne dopasowanie wielkości liter, jak jest zdefiniowany w źródle.

- Nie można odnaleźć modułu lub biblioteki DLL.

   Sprawdź pełną nazwę ścieżki określonego modułu lub biblioteki DLL.

Ten błąd jest taka sama jak CAN0036.