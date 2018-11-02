---
title: Brak połączenia
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 9775270c5c1fb0b6758f994c432104d75e19d38d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505082"
---
# <a name="no-linkage"></a>Brak połączenia

Jeśli nie ma deklarację dla identyfikatora w bloku `extern` Specyfikator klasy magazynowania, identyfikator ma bez połączenia i jest unikatowy dla funkcji.

Następujące identyfikatory są bez połączenia:

- Identyfikator zadeklarowany za nic innego niż obiekt lub funkcja

- Identyfikator zadeklarowany jako parametr funkcji

- Identyfikator o zakresie bloku dla obiektu zadeklarowana bez `extern` Specyfikator klasy magazynowania

Jeśli identyfikator ma bez połączenia, Zadeklarowanie tej samej nazwie ponownie (w deklarator lub Specyfikator typu), w tym samym poziomie zakresu generuje błąd zmiana definicji symbolu.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)