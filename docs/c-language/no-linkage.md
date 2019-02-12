---
title: Brak połączenia
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152849"
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
