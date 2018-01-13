---
title: "Polecenia w pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5361012fd388f49d8eb956ec1a4fa1bdd53a2dcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="commands-in-a-makefile"></a>Polecenia w pliku reguł programu Make
Opis reguły blokowanie lub wnioskowania określa blok polecenia do uruchomienia, jeśli zależność jest nieaktualne. NMAKE Wyświetla każde polecenie przed uruchomieniem go, chyba że/s, **. DYSKRETNEJ**, **! CMDSWITCHES**, lub @ jest używany. NMAKE szuka reguły wnioskowania dopasowania, jeśli blok opis nie następuje blok poleceń.  
  
 Blok poleceń zawiera co najmniej jedno polecenie, każdego w osobnym wierszu. Nie pusty wiersz może wystąpić między zależności lub reguły i blok poleceń. Jednak wiersz zawierający tylko spacji ani karty mogą być wyświetlane; Ten wiersz jest interpretowane jako polecenie null, a nie występują błędy. Puste wiersze są dozwolone między wiersze polecenia.  
  
 Wiersz polecenia rozpoczyna się od spacji lub kart. Ukośnik odwrotny (\), a następnie znaku nowego wiersza jest interpretowana jako miejsca w poleceniu; Użyj ukośnikiem na końcu wiersza, aby kontynuować do następnego wiersza polecenia. NMAKE interpretuje ukośniku odwrotnym dosłownie innych znaków, w tym spację lub tabulator, jeśli ukośniku odwrotnym.  
  
 Polecenie poprzedzonego średnikami (;) może wystąpić reguł wiersza lub wnioskowania zależności, czy następuje blok poleceń:  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Modyfikatory poleceń](../build/command-modifiers.md)  
  
 [Składnia nazwy pliku części](../build/filename-parts-syntax.md)  
  
 [Pliki wbudowane w pliku reguł programu make](../build/inline-files-in-a-makefile.md)  
  
## <a name="see-also"></a>Zobacz też  
 [NMAKE — dokumentacja](../build/nmake-reference.md)