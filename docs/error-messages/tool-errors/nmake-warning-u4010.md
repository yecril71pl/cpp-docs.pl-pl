---
title: "Ostrzeżenie NMAKE U4010 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2d90e95a3417241991eb01f0ec718d75cd8558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4010"></a>Ostrzeżenie NMAKE U4010
'target': kompilacja nie powiodła się; /K określony, kontynuowanie...  
  
 Polecenia w bloku poleceń dla danego obiektu docelowego zwróciło kod zakończenia różną od zera. Opcję/k informację NMAKE kontynuować przetwarzanie niepowiązanych części kompilacji i wydania kod zakończenia 1, po zakończeniu sesji NMAKE.  
  
 W przypadku danego obiektu docelowego, sam zależnych dla innego obiektu docelowego, NMAKE generuje ostrzeżenie [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) po to ostrzeżenie.