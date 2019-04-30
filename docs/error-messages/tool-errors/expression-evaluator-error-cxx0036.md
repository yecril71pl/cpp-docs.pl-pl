---
title: Błąd CXX0036 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: d7961d92760cc5ac325b4bc9f187d4ee2298479a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397032"
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