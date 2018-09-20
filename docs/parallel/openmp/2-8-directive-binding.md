---
title: 2.8 powiązania dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b702b17e01bb8d4625a837abdb71086113e68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415905"
---
# <a name="28-directive-binding"></a>2.8 Powiązania dyrektywy

Dynamiczne powiązanie dyrektyw określających muszą być zgodne z następującymi zasadami:

- **Dla**, **sekcje**, **pojedynczego**, **wzorca**, i **barierę** dyrektywy powiązać dynamicznie otaczający **równoległe**, jeśli taki istnieje, niezależnie od wartości dowolnych **Jeśli** klauzula, która może znajdować się w tej dyrektywy. Jeśli obecnie jest wykonywana nie równoległego regionu, dyrektywy są wykonywane przez zespół składa się z głównego wątku.

- **Uporządkowane** dyrektywy wiąże dynamicznie otaczający **dla**.

- **Atomic** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **atomic** dyrektywy w wszystkie wątki, nie tylko zespół.

- **Krytyczne** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **krytyczne** dyrektywy w wszystkie wątki, nie tylko zespół.

- Dyrektywy może nigdy nie mają powiązań każdej dyrektywy poza najbardziej dynamicznie otaczający **równoległe**.