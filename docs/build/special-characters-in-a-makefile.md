---
title: Znaki specjalne w pliku reguł programu make | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 157f9ed499ef7a0ac9efdd6bebe118ca593acabb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380462"
---
# <a name="special-characters-in-a-makefile"></a>Znaki specjalne w pliku reguł programu Make
Aby użyć znaków specjalnych w NMAKE jako literału znaku, umieść daszek (^) przed nim. NMAKE ignoruje daszka poprzedzających innych znaków. Znaki specjalne są:  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 Daszek (^) w ciągu w cudzysłowie jest traktowany jako znak literału karetki. Karetkę na końcu wiersza wstawia znaku nowego wiersza literału ciągu lub makra.  
  
 W makrach, ukośnik odwrotny (\\) zostały wykonane przez nowym wierszem znak zastępuje się spacją.  
  
 W poleceniach symbol procentu (%) jest określenie pliku. Do reprezentowania % dosłownie w poleceniu, zamiast jedno należy określić podwójnego znaku procentu (%). W innych sytuacjach NMAKE interpretuje pojedynczego % dosłownie, ale zawsze interpretuje wartość o podwójnej precyzji %% jako pojedynczy %. W związku z tym do reprezentowania literału %%, określ albo znaki procent trzech %%%, lub wartość procentowa czterech znaków, %%%.  
  
 Aby użyć dolara ($) jako znak literałowy, w poleceniu, określ dwa dolara ($). Ta metoda umożliwia również w innych sytuacjach, w którym ^ $ działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)