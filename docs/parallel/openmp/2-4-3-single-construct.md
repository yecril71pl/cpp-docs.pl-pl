---
title: 2.4.3 pojedyncza konstrukcja | Dokumentacja firmy Microsoft
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc551986f149bda668c438ac5f51d01d530c51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="243-single-construct"></a>2.4.3 Pojedyncza konstrukcja
**Pojedynczego** dyrektywy identyfikuje konstrukcję, która określa, że skojarzona strukturalnego bloku jest wykonywana tylko jednego wątku w zespole (niekoniecznie wątku głównego). Składnia **pojedynczego** dyrektywy wygląda następująco:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 Klauzuli jest jednym z następujących czynności:  
  
 **prywatne (** *zmiennej listy* **)**  
  
 **firstprivate (** *zmiennej listy* **)**  
  
 **copyprivate (** *zmiennej listy* **)**  
  
 **nowait**  
  
 Brak niejawnego bariery po **pojedynczego** skonstruować, chyba że **nowait** jest określona klauzula.  
  
 Ograniczenia **pojedynczego** dyrektywy są następujące:  
  
-   Tylko jeden **nowait** klauzula może występować w **pojedynczego** dyrektywy.  
  
-   **Copyprivate** nie można użyć klauzuli z **nowait** klauzuli.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **prywatne**, **firstprivate**, i **copyprivate** klauzule, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.