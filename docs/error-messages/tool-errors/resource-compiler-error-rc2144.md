---
title: Błąd kompilatora zasobów RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: deabd639e04d5b78b398cda9245e9726e2124740
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642926"
---
# <a name="resource-compiler-error-rc2144"></a>Błąd kompilatora zasobów RC2144

PODSTAWOWY identyfikator języka nie jest liczbą

PODSTAWOWY identyfikator języka musi być identyfikatorem szesnastkowe języka. Zobacz [język i Kraj/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) w *odwołanie do biblioteki wykonawczej* listę poprawnych identyfikatorów języka.

Ten błąd może również wystąpić, jeśli zasoby zostały dodane i usunięta z. Plik RC przy użyciu narzędzia. Aby rozwiązać ten problem, Otwórz. RC plik ręcznie w edytorze tekstów i wyczyścić wszystkie nieużywane zasoby.