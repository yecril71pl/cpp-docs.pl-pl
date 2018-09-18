---
title: Błąd BSCMAKE BK1513 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68f49ce11c95672abd40ecbaf1873a564a3912e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118807"
---
# <a name="bscmake-error-bk1513"></a>Błąd BSCMAKE BK1513

nieprzyrostowa aktualizacja wymaga wszystkich. Pliki SBR

BSCMAKE nie może utworzyć nowego pliku przeglądania informacji (.bsc), ponieważ jeden lub więcej plików SBR są obcinane. Aby znaleźć nazwy plików SBR obcięty, przeczytaj [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) ostrzeżenia, dołączone do tego błędu.

BSCMAKE można zaktualizować pliku .bsc przy użyciu pliku SBR obcięty, ale nie można utworzyć nowy. BSCMAKE może utworzyć nowego pliku .bsc z następujących powodów:

- Brak pliku .bsc.

- Problem nie określono nazwy pliku dla pliku .bsc.

- Plik .bsc uszkodzony.

Aby rozwiązać ten problem, Usuń pliki SBR obcięte i ponownej kompilacji, lub wyczyść rozwiązanie i ponownie skompilować. (W środowisku IDE, wybierz **kompilacji**, **czyste rozwiązanie**, a następnie wybierz **kompilacji**, **Kompiluj rozwiązanie**.)