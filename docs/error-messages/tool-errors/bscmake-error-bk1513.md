---
title: Błąd BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: c02e9b47b3d32e4d21914188b96913d6dff03127
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477223"
---
# <a name="bscmake-error-bk1513"></a>Błąd BSCMAKE BK1513

nieprzyrostowa aktualizacja wymaga wszystkich. Pliki SBR

BSCMAKE nie może utworzyć nowego pliku przeglądania informacji (.bsc), ponieważ jeden lub więcej plików SBR są obcinane. Aby znaleźć nazwy plików SBR obcięty, przeczytaj [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) ostrzeżenia, dołączone do tego błędu.

BSCMAKE można zaktualizować pliku .bsc przy użyciu pliku SBR obcięty, ale nie można utworzyć nowy. BSCMAKE może utworzyć nowego pliku .bsc z następujących powodów:

- Brak pliku .bsc.

- Problem nie określono nazwy pliku dla pliku .bsc.

- Plik .bsc uszkodzony.

Aby rozwiązać ten problem, Usuń pliki SBR obcięte i ponownej kompilacji, lub wyczyść rozwiązanie i ponownie skompilować. (W środowisku IDE, wybierz **kompilacji**, **czyste rozwiązanie**, a następnie wybierz **kompilacji**, **Kompiluj rozwiązanie**.)