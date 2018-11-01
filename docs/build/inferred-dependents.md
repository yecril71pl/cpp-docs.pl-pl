---
title: Zależności wywnioskowane
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 958a33c29be0d68fee1044fff1d81235ea9370c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641379"
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane

Wywnioskowane zależnych od ustawień lokalnych jest tworzony na podstawie reguły wnioskowania i zostanie wykonane przed jawne zależności. W przypadku przestarzałe względem jego element docelowy wywnioskowane zależnych od ustawień lokalnych NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależnych od ustawień lokalnych nie istnieje lub jest nieaktualna w odniesieniu do jego własnej zależności, NMAKE najpierw aktualizuje wywnioskowane zależnych od ustawień lokalnych. Aby uzyskać więcej informacji na temat wywnioskowane zobacz [reguły wnioskowania](../build/inference-rules.md).

## <a name="see-also"></a>Zobacz też

[Zależności](../build/dependents.md)