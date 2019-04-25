---
title: Brak połączenia
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232392"
---
# <a name="no-linkage"></a>Brak połączenia

Jeśli nie ma deklarację dla identyfikatora w bloku `extern` Specyfikator klasy magazynowania, identyfikator ma bez połączenia i jest unikatowy dla funkcji.

Następujące identyfikatory są bez połączenia:

- Identyfikator zadeklarowany za nic innego niż obiekt lub funkcja

- Identyfikator zadeklarowany jako parametr funkcji

- Identyfikator o zakresie bloku dla obiektu zadeklarowana bez `extern` Specyfikator klasy magazynowania

Jeśli identyfikator ma bez połączenia, Zadeklarowanie tej samej nazwie ponownie (w deklarator lub Specyfikator typu), w tym samym poziomie zakresu generuje błąd zmiana definicji symbolu.

## <a name="see-also"></a>Zobacz także

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
