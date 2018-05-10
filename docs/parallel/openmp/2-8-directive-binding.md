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
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="28-directive-binding"></a>2.8 Powiązania dyrektywy
Wiązania dynamicznego dyrektyw muszą być zgodne z następującymi zasadami:  
  
-   **Dla**, **sekcje**, **pojedynczego**, **wzorca**, i **bariery** dyrektywy powiązać dynamicznie otaczającej **równoległych**, jeśli istnieje, niezależnie od wartości dowolnego **Jeśli** klauzuli, która może znajdować się na tej dyrektywy. Jeśli nie równoległego regionu nie jest aktualnie wykonywane, dyrektywy są wykonywane przez zespół składa się z głównego wątku.  
  
-   **Uporządkowane** dyrektywy wiąże dynamicznie otaczającego **dla**.  
  
-   **Atomic** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **atomic** dyrektywy w wszystkie wątki, nie tylko zespołu.  
  
-   **Krytyczne** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **krytyczne** dyrektywy w wszystkie wątki, nie tylko zespołu.  
  
-   Dyrektywy może nigdy nie mają powiązań jakiejkolwiek dyrektywy poza najbardziej dynamicznie otaczającej **równoległych**.