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
ms.openlocfilehash: 7ed21327028fc9849f6e0694bb82ae34c6084842
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301466"
---
# <a name="linker-tools-error-lnk1264"></a>Błąd narzędzi konsolidatora LNK1264
/LTCG:PGINSTRUMENT określono, lecz generowanie kodu nie jest wymagane; Instrumentacja nie powiodła się  
  
 **/LTCG:PGINSTRUMENT** został określony, ale nie znaleziono plików .obj, które zostały skompilowane z [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentacja nie może przyjąć miejscu i łącze nie powiodło się. Musi istnieć co najmniej jeden plik .obj w wierszu polecenia, który jest skompilowana przy użyciu **/GL** , dzięki czemu może wystąpić Instrumentację.  
  
 Optymalizacja sterowana profilem (PGO) jest dostępna tylko w 64-bitowych kompilatory.