---
title: "Błąd narzędzi konsolidatora LNK1264 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f590de75998becb9c03c73ac3083b04445a02156
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1264"></a>Błąd narzędzi konsolidatora LNK1264
/LTCG:PGINSTRUMENT określono, lecz generowanie kodu nie jest wymagane; Instrumentacja nie powiodła się  
  
 **/LTCG:PGINSTRUMENT** został określony, ale nie znaleziono plików .obj, które zostały skompilowane z [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentacja nie może przyjąć miejscu i łącze nie powiodło się. Musi istnieć co najmniej jeden plik .obj w wierszu polecenia, który jest skompilowana przy użyciu **/GL** , dzięki czemu może wystąpić Instrumentację.  
  
 Optymalizacja sterowana profilem (PGO) jest dostępna tylko w 64-bitowych kompilatory.