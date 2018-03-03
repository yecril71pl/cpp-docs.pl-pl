---
title: "2.8 powiązania dyrektywy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 731c509c0c2f300d7a9d4e39261ffedd1c22a094
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="28-directive-binding"></a>2.8 Powiązania dyrektywy
Wiązania dynamicznego dyrektyw muszą być zgodne z następującymi zasadami:  
  
-   **Dla**, **sekcje**, **pojedynczego**, **wzorca**, i **bariery** dyrektywy powiązać dynamicznie otaczającej **równoległych**, jeśli istnieje, niezależnie od wartości dowolnego **Jeśli** klauzuli, która może znajdować się na tej dyrektywy. Jeśli nie równoległego regionu nie jest aktualnie wykonywane, dyrektywy są wykonywane przez zespół składa się z głównego wątku.  
  
-   **Uporządkowane** dyrektywy wiąże dynamicznie otaczającego **dla**.  
  
-   **Atomic** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **atomic** dyrektywy w wszystkie wątki, nie tylko zespołu.  
  
-   **Krytyczne** dyrektywy wymusza wyłącznego dostępu w odniesieniu do **krytyczne** dyrektywy w wszystkie wątki, nie tylko zespołu.  
  
-   Dyrektywy może nigdy nie mają powiązań jakiejkolwiek dyrektywy poza najbardziej dynamicznie otaczającej **równoległych**.