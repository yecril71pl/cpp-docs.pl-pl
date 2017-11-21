---
title: "Modyfikatory poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c1790a89381219191f273cfacb16e69b1495171a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-modifiers"></a>Modyfikatory poleceń
Można określić co najmniej jeden Modyfikatory poleceń poprzedzających polecenia, opcjonalnie oddzielone spacjami lub kart. Podobnie jak w przypadku poleceń, można wcięty modyfikatorów.  
  
|Modyfikator|Cel|  
|--------------|-------------|  
|@*polecenie*|Uniemożliwia wyświetlanie polecenia. Wyświetlanie polecenia nie został on wstrzymany. Domyślnie NMAKE zwraca wszystkie wykonanego polecenia. Aby pominąć wyświetlania dla całego pliku reguł programu make; Użyj/s Użyj **. DYSKRETNEJ** do pomijania wyświetlania części pliku reguł programu make.|  
|**-**[`number` ]*polecenia*|Wyłącza sprawdzanie błędów *polecenia*. Domyślnie NMAKE zostaje zatrzymana, gdy polecenie zwraca kod zakończenia różną od zera. IF -`number` jest używana, NMAKE zatrzymuje, jeśli kod zakończenia przekracza `number`. Spacji ani karty nie mogą występować między kreska i *numer.* Co najmniej jedną spację lub tabulator musi występować między `number` i *polecenia*. Użyj /I, aby wyłączyć sprawdzanie błędów dotyczących całego pliku reguł programu make; Użyj **. Ignoruj** Aby wyłączyć sprawdzanie błędów dotyczących część pliku reguł programu make.|  
|**!** *polecenie*|Wykonuje *polecenia* dla każdego pliku zależnego Jeśli *polecenia* używa  **$ \* \***  (wszystkie pliki zależne w zależności) lub **$?** (wszystkie pliki zależne w zależności z sygnaturą czasową nowsze niż wersja docelowa).|  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia w pliku reguł programu make](../build/commands-in-a-makefile.md)