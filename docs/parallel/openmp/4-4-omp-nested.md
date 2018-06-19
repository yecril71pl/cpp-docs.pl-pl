---
title: 4.4 OMP_NESTED | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690273"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED` Zmiennej środowiskowej Włącza lub wyłącza zagnieżdżonych równoległości, chyba że zagnieżdżonych równoległości jest włączone lub wyłączone przez wywołanie metody `o` **mp_set_nested** procedury biblioteki. Jeśli ustawioną **TRUE**, zagnieżdżonych równoległości jest włączone; jeśli wartość jest ustawiona na **FALSE**, zagnieżdżonych równoległości jest wyłączona. Wartość domyślna to **FALSE**.  
  
 Przykład:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Granic odwołania:  
  
-   `omp_set_nested` funkcji, zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40.