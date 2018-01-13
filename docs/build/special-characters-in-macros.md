---
title: Znaki specjalne w makrach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d954abc593fcba3887da4f7ee4bd5ce1e443e18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="special-characters-in-macros"></a>Znaki specjalne w makrach
Numer podpisać (#) po definicji określa komentarz. Aby określić znak numeru literału w makrze, użyj daszek (^), podobnie jak w ^ #.  
  
 Znak dolara ($) określa wywołanie makra. Aby określić $ literału, użyj $$.  
  
 Aby rozszerzyć definicji do nowego wiersza, kończyć wiersz z ukośnik odwrotny (\\). Po wywołaniu makra znaku ukośnika odwrotnego plus nowego wiersza zostanie zastąpiony się spacją. Aby określić literału ukośnikiem na końcu wiersza, należy poprzedzić go daszek (^), lub po nim ze specyfikatorem komentarza (#).  
  
 Aby określić znak nowego wiersza literału, Zakończ wiersz z daszek (^), jak w programie:  
  
```  
CMDS = cls^  
dir  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)