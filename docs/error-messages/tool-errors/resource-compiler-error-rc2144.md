---
title: Błąd kompilatora zasobów RC2144 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f9eb2b25919a2336c36a459ef41eece447a490
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080496"
---
# <a name="resource-compiler-error-rc2144"></a>Błąd kompilatora zasobów RC2144

PODSTAWOWY identyfikator języka nie jest liczbą

PODSTAWOWY identyfikator języka musi być identyfikatorem szesnastkowe języka. Zobacz [język i Kraj/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) w *odwołanie do biblioteki wykonawczej* listę poprawnych identyfikatorów języka.

Ten błąd może również wystąpić, jeśli zasoby zostały dodane i usunięta z. Plik RC przy użyciu narzędzia. Aby rozwiązać ten problem, Otwórz. RC plik ręcznie w edytorze tekstów i wyczyścić wszystkie nieużywane zasoby.