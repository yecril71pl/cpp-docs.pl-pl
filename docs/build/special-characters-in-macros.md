---
title: Znaki specjalne w makrach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c271d2f39a4d81776c06a107616170192e82d40d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380176"
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