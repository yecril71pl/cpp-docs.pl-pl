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
ms.openlocfilehash: 631c5631b60f0e05dd1f1541facc767f35944d3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701483"
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane

Wywnioskowane zależnych od ustawień lokalnych jest tworzony na podstawie reguły wnioskowania i zostanie wykonane przed jawne zależności. W przypadku przestarzałe względem jego element docelowy wywnioskowane zależnych od ustawień lokalnych NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależnych od ustawień lokalnych nie istnieje lub jest nieaktualna w odniesieniu do jego własnej zależności, NMAKE najpierw aktualizuje wywnioskowane zależnych od ustawień lokalnych. Aby uzyskać więcej informacji na temat wywnioskowane zobacz [reguły wnioskowania](../build/inference-rules.md).

## <a name="see-also"></a>Zobacz też

[Zależności](../build/dependents.md)