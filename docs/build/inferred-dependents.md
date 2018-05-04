---
title: Wywnioskowane zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86ed1a8fe6c97ae11af50f59cb639ef6fd7c1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane
Wywnioskowane zależnych pochodzi z reguły wnioskowania i jest oceniane przed jawne zależności. W przypadku nieaktualne względem jego docelowy wnioskowany zależne od NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależne od nie istnieje lub jest nieaktualny w stosunku do jego własnej zależności, NMAKE najpierw aktualizuje wnioskowany zależnego. Aby uzyskać więcej informacji na temat zależności wywnioskowane, zobacz [zasady wnioskowania](../build/inference-rules.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zależności](../build/dependents.md)