---
title: Zależności wywnioskowane
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291538"
---
# <a name="inferred-dependents"></a>Zależności wywnioskowane

Wywnioskowane zależnych od ustawień lokalnych jest tworzony na podstawie reguły wnioskowania i zostanie wykonane przed jawne zależności. W przypadku przestarzałe względem jego element docelowy wywnioskowane zależnych od ustawień lokalnych NMAKE wywołuje blok poleceń dla zależności. Wywnioskowane zależnych od ustawień lokalnych nie istnieje lub jest nieaktualna w odniesieniu do jego własnej zależności, NMAKE najpierw aktualizuje wywnioskowane zależnych od ustawień lokalnych. Aby uzyskać więcej informacji na temat wywnioskowane zobacz [reguły wnioskowania](inference-rules.md).

## <a name="see-also"></a>Zobacz także

[Zależności](dependents.md)
