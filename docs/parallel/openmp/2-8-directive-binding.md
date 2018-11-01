---
title: 2.8 Powiązania dyrektywy
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528625"
---
# <a name="28-directive-binding"></a>2.8 Powiązania dyrektywy

Dynamiczne powiązanie dyrektyw określających muszą być zgodne z następującymi zasadami:

- **Dla**, **sekcje**, **pojedynczego**, **wzorca**, i **barierę** dyrektywy powiązać dynamicznie otaczający **równoległe**, jeśli taki istnieje, niezależnie od wartości dowolnych **Jeśli** klauzula, która może znajdować się w tej dyrektywy. Jeśli obecnie jest wykonywana nie równoległego regionu, dyrektywy są wykonywane przez zespół składa się z głównego wątku.

- **Uporządkowane** dyrektywy wiąże dynamicznie otaczający **dla**.

- **Atomic** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **atomic** dyrektywy w wszystkie wątki, nie tylko zespół.

- **Krytyczne** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **krytyczne** dyrektywy w wszystkie wątki, nie tylko zespół.

- Dyrektywy może nigdy nie mają powiązań każdej dyrektywy poza najbardziej dynamicznie otaczający **równoległe**.