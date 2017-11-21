---
title: "Pierwszeństwo w definicjach makr | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a71f69f141e92e7134d6048de67301198a667c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="precedence-in-macro-definitions"></a>Pierwszeństwo w definicjach makr
Jeśli makro ma wiele definicji, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa, w kolejności malejącej:  
  
1.  Makra zdefiniowane w wierszu polecenia  
  
2.  Makra zdefiniowane w pliku reguł programu make lub dołączyć plik  
  
3.  Dziedziczony makra zmiennych środowiskowych  
  
4.  Makra zdefiniowane w pliku Tools.ini  
  
5.  Wstępnie zdefiniowane makra, takich jak [DW](../build/command-macros-and-options-macros.md) i [AS](../build/command-macros-and-options-macros.md)  
  
 /E umożliwia spowodować makra odziedziczone zmiennych środowiskowych w celu zastąpienia pliku reguł programu make makra o takiej samej nazwie. Użyj **! UNDEF** do przesłonięcia wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)