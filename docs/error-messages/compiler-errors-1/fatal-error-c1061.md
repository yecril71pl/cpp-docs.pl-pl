---
title: Błąd krytyczny C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 1733a13e697af775653609ddfcc22f7297dad240
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661178"
---
# <a name="fatal-error-c1061"></a>Błąd krytyczny C1061

limit kompilatora : blokuje zbyt głębokie zagnieżdżanie

Zagnieżdżanie bloków kodu przekracza limit 128 poziomów zagnieżdżenia. Jest to stały limit w kompilatorze dla C i C++, w zestawie narzędzi 32-bitowych i 64-bitowych. Liczba poziomów zagnieżdżenia może być zwiększana przez wszystko, co tworzy zakres lub blok. Na przykład, wszystkie przestrzenie nazw, stosowanie dyrektyw, rozszerzenia preprocesora, rozszerzenie szablonu, obsługa wyjątków, konstrukcje pętli i klauzule else-if mogą zwiększyć poziom zagnieżdżenia, jaki widzi kompilator.

Aby naprawić ten błąd, musisz wykonać refaktoryzację kodu. W każdym przypadku głęboko zagnieżdżony kod trudno zrozumieć i poprawić. Refaktoryzacja kodu, której celem jest zmniejszenie liczby poziomów zagnieżdżenia, może poprawić jakość kodu i uprościć zarządzanie nim. Podziel głęboko zagnieżdżony kod na funkcje, które są wywoływane z oryginalnego kontekstu. Ogranicz liczbę pętli lub połączonych klauzul else-if w bloku.