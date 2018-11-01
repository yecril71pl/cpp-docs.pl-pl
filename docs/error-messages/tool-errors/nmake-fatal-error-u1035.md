---
title: Błąd krytyczny NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589492"
---
# <a name="nmake-fatal-error-u1035"></a>Błąd krytyczny NMAKE U1035

Błąd składniowy: oczekiwano ":" lub "=" separator

Albo dwukropka (**:**) lub znak równości (**=**) był oczekiwany.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Dwukropek nie korzystał z obiektu docelowego.

1. Dwukropek i brak miejsca (na przykład a:), a następnie element docelowy jedną literę. NMAKE interpretuje ją jako specyfikację dysku.

1. Dwukropek nie korzystał z reguły wnioskowania.

1. Znak równości nie nastąpiła definicji makra.

1. Znak, a następnie kreski ułamkowej odwróconej (**\\**) który został użyty do kontynuowania polecenia do nowego wiersza.

1. Pojawiły się ciąg, który nie korzystał z dowolnej reguły składni NMAKE.

1. Pliku reguł programu make został sformatowany przy użyciu edytora tekstu.