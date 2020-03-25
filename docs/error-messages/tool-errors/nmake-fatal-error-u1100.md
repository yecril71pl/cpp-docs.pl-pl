---
title: Błąd krytyczny NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193267"
---
# <a name="nmake-fatal-error-u1100"></a>Błąd krytyczny NMAKE U1100

makro "Macroname" jest niedozwolone w kontekście reguły wsadowej "Rule"

NMAKE generuje ten błąd, gdy blok poleceń reguły trybu wsadowego bezpośrednio lub pośrednio odwołuje się do specjalnego makra pliku, który nie jest $ <.

$ < to jedyne dozwolone makro dla reguł trybu wsadowego.
