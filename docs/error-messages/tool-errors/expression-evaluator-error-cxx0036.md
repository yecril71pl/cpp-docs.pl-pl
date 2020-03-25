---
title: Błąd CXX0036 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195503"
---
# <a name="expression-evaluator-error-cxx0036"></a>Błąd CXX0036 programu Expression Evaluator

zły kontekst {...} specyfikacja

Ten komunikat może być generowany przez dowolny z kilku błędów podczas korzystania z operatora kontekstu ( **{}** ).

- Składnia operatora kontekstu ( **{}** ) została nieprawidłowo określona.

   Składnia operatora kontekstu to:

     {*Function*,*module*,*dll*} *wyrażenie*

   Określa kontekst *wyrażenia*. Operator kontekstu ma takie samo pierwszeństwo i użycie jak rzutowanie typu.

   Końcowe przecinki można pominąć. Jeśli którakolwiek z *funkcji*, *modułów*lub *dll* zawiera przecinek literału, należy ująć całą nazwę w nawiasy.

- Nazwa funkcji została wpisana niepoprawnie lub nie istnieje w określonym module lub bibliotece dołączanej dynamicznie.

   Ponieważ język C jest rozróżniana wielkość liter, *Funkcja* musi być określona w dokładnie takim przypadku, jak jest zdefiniowana w źródle.

- Nie można znaleźć modułu lub biblioteki DLL.

   Sprawdź pełną nazwę ścieżki określonego modułu lub biblioteki DLL.

Ten błąd jest identyczny z CAN0036.
