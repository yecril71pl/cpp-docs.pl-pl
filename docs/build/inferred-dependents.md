---
title: "Wywnioskowane zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eaf75c067b2e96e5ae4a893b56376bfc1b9bd1e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane
Wywnioskowane zależnych pochodzi z reguły wnioskowania i jest oceniane przed jawne zależności. W przypadku nieaktualne względem jego docelowy wnioskowany zależne od NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależne od nie istnieje lub jest nieaktualny w stosunku do jego własnej zależności, NMAKE najpierw aktualizuje wnioskowany zależnego. Aby uzyskać więcej informacji na temat zależności wywnioskowane, zobacz [zasady wnioskowania](../build/inference-rules.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zależności](../build/dependents.md)