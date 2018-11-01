---
title: Błąd narzędzi konsolidatora LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: ca17b6946b9e988507af2786825223e042356d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505095"
---
# <a name="linker-tools-error-lnk1264"></a>Błąd narzędzi konsolidatora LNK1264

Pginstrument określone, lecz generowanie kodu nie jest wymagane; Instrumentacja nie powiodła się

**Pginstrument** został określony, ale nie znaleziono plików .obj, które zostały skompilowane przy użyciu [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentacja nie można przyjąć miejsce i łącza nie powiodło się. Musi istnieć co najmniej jeden plik .obj w wierszu polecenia, który został skompilowany z **/GL** tak, może wystąpić Instrumentację.

Optymalizacja z przewodnikiem profilu (PGO) jest dostępna tylko w kompilatorach, 64-bitowych.