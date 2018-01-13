---
title: "Składnia nazwy pliku części | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a481f8c461cb4fddd4acb090edb2f2b5fd18636d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="filename-parts-syntax"></a>Składnia nazwy pliku-części
Składnia nazwy pliku części w poleceniach reprezentuje składniki pierwszy filename zależne (które mogą być domniemanych zależnych). Składniki filename są dysku pliku, ścieżka, nazwie podstawowej i rozszerzenia określone, nie, które znajdują się na dysku. Użyj **%s** do reprezentowania pełną nazwę pliku. Użyj **% &#124;** [*części*]**F** (pionowy pasek symbol procentu następuje znak) do reprezentowania części nazwy pliku, gdzie *części* może być zero lub więcej z następujących w dowolnej kolejności.  
  
|Litera|Opis|  
|------------|-----------------|  
|Brak litery|Pełna nazwa (taki sam jak **%s**)|  
|**d**|Dysk|  
|**p**|Ścieżka|  
|**f**|Nazwa podstawowa pliku|  
|**e**|Rozszerzenie pliku|  
  
 Na przykład, jeśli nazwa pliku jest c:\prog.exe:  
  
-   %s będzie c:\prog.exe  
  
-   % &#124; F będzie c:\prog.exe  
  
-   % &#124; dF będzie c  
  
-   % &#124; pF będzie c:\  
  
-   % &#124; fF będzie programu  
  
-   % &#124; eF będzie exe  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia w pliku reguł programu Make](../build/commands-in-a-makefile.md)