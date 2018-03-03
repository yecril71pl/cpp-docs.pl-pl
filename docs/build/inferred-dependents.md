---
title: "Wywnioskowane zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 410e52dd9ee9605f6e29b81491bda0f4883e1cf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane
Wywnioskowane zależnych pochodzi z reguły wnioskowania i jest oceniane przed jawne zależności. W przypadku nieaktualne względem jego docelowy wnioskowany zależne od NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależne od nie istnieje lub jest nieaktualny w stosunku do jego własnej zależności, NMAKE najpierw aktualizuje wnioskowany zależnego. Aby uzyskać więcej informacji na temat zależności wywnioskowane, zobacz [zasady wnioskowania](../build/inference-rules.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zależności](../build/dependents.md)