---
title: Pierwszeństwo w definicjach makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce6f0acc898dc719d2252d5cc59dff92bda4a98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368616"
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