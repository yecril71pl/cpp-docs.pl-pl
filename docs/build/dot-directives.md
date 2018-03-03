---
title: Dyrektywy dot | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9958b13a6f06b0024ec2d4dd304abfe93b16741e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dot-directives"></a>Dyrektywy Dot
Określ dyrektywy dot poza blokiem opis na początku wiersza. Dyrektywy dot rozpoczynać się kropką (. ) i są z dwukropkiem (:). Karty i spacje są dozwolone. Nazwy dyrektywy dot jest uwzględniana wielkość liter i wielkimi literami.  
  
|Dyrektywy|Cel|  
|---------------|-------------|  
|**. IGNORUJ:**|Ignoruje kody wyjścia niezerową zwracane przez polecenia od miejsca, jest określana na końcu pliku reguł programu make. Domyślnie NMAKE zostaje zatrzymana, jeśli polecenie zwróci kod zakończenia różną od zera. Aby przywrócić sprawdzanie błędów, użyj **! CMDSWITCHES**. Aby zignorować kod zakończenia polecenia, użyj modyfikatora kreski (-). Aby Ignoruj kody wyjścia dla całego pliku, użyj / I.|  
|**. SZLACHETNYCH:** *elementów docelowych*|Zachowuje *cele* na dysku czy polecenia ich aktualizacji są zatrzymane; nie ma efektu Jeśli polecenie obsługi przerwań przez usunięcie pliku. Rozdziel nazwy docelowej z spacji lub kart. Domyślnie NMAKE usuwa element docelowy, jeśli kompilacja zostanie przerwana przez kombinację klawiszy CTRL + C lub CTRL + BREAK. Każdy stosowania **. CENNY** ma zastosowanie do całego pliku reguł programu make; kumulują się wielu specyfikacji.|  
|**. CICHY:**|Pomija wyświetlanie wykonać poleceń od miejsca, jest określana na końcu pliku reguł programu make. Domyślnie NMAKE Wyświetla polecenia, które wywołuje. Aby przywrócić wyświetlania, należy użyć **! CMDSWITCHES**. Aby uniknąć wyświetlania pojedynczego polecenia, użyj  **@**  modyfikator. Aby uniknąć wyświetlania dla całego pliku, użyj/S.|  
|**. SUFIKSY NAZW:**`list`|Lista rozszerzeń do dopasowania reguła wnioskowania; wstępnie zdefiniowane uwzględnienie następujących rozszerzeń: .exe .obj .asm .c .cpp .cxx .bas .cbl .for .pas .res .rc .f .f90|  
  
 Aby zmienić **. SUFIKSY** listy kolejności lub aby określić nową listę, wyczyść listy i określ nowe ustawienie. Aby wyczyścić listę, należy określić Brak rozszerzeń po dwukropkiem:  
  
```  
.SUFFIXES :  
```  
  
 Aby dodać dodatkowe sufiksy na końcu listy, określ  
  
```  
.SUFFIXES : suffixlist  
```  
  
 gdzie *suffixlist* znajduje się lista sufiksów oddzielone spacjami lub kart. Aby wyświetlić bieżące ustawienie **. SUFIKSY**, uruchom NMAKE z/p.  
  
## <a name="see-also"></a>Zobacz też  
 [NMAKE — dokumentacja](../build/nmake-reference.md)