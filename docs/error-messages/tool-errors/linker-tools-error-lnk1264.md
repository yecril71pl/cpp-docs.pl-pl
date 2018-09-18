---
title: Błąd narzędzi konsolidatora LNK1264 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8232e83774dc53755b77ad9c8b3bbb2a0bcc6ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102752"
---
# <a name="linker-tools-error-lnk1264"></a>Błąd narzędzi konsolidatora LNK1264

Pginstrument określone, lecz generowanie kodu nie jest wymagane; Instrumentacja nie powiodła się

**Pginstrument** został określony, ale nie znaleziono plików .obj, które zostały skompilowane przy użyciu [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentacja nie można przyjąć miejsce i łącza nie powiodło się. Musi istnieć co najmniej jeden plik .obj w wierszu polecenia, który został skompilowany z **/GL** tak, może wystąpić Instrumentację.

Optymalizacja z przewodnikiem profilu (PGO) jest dostępna tylko w kompilatorach, 64-bitowych.