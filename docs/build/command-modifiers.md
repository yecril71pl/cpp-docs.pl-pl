---
title: Modyfikatory poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3739c053797bdccd08310e17bf669413ead0db48
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="command-modifiers"></a>Modyfikatory poleceń
Można określić co najmniej jeden Modyfikatory poleceń poprzedzających polecenia, opcjonalnie oddzielone spacjami lub kart. Podobnie jak w przypadku poleceń, można wcięty modyfikatorów.  
  
|Modyfikator|Cel|  
|--------------|-------------|  
|@*polecenie*|Uniemożliwia wyświetlanie polecenia. Wyświetlanie polecenia nie został on wstrzymany. Domyślnie NMAKE zwraca wszystkie wykonanego polecenia. Aby pominąć wyświetlania dla całego pliku reguł programu make; Użyj/s Użyj **. DYSKRETNEJ** do pomijania wyświetlania części pliku reguł programu make.|  
|**-**[`number` ]*polecenia*|Wyłącza sprawdzanie błędów *polecenia*. Domyślnie NMAKE zostaje zatrzymana, gdy polecenie zwraca kod zakończenia różną od zera. IF -`number` jest używana, NMAKE zatrzymuje, jeśli kod zakończenia przekracza `number`. Spacji ani karty nie mogą występować między kreska i *numer.* Co najmniej jedną spację lub tabulator musi występować między `number` i *polecenia*. Użyj /I, aby wyłączyć sprawdzanie błędów dotyczących całego pliku reguł programu make; Użyj **. Ignoruj** Aby wyłączyć sprawdzanie błędów dotyczących część pliku reguł programu make.|  
|**!** *polecenie*|Wykonuje *polecenia* dla każdego pliku zależnego Jeśli *polecenia* używa **$ \* \*** (wszystkie pliki zależne w zależności) lub **$?** (wszystkie pliki zależne w zależności z sygnaturą czasową nowsze niż wersja docelowa).|  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia w pliku reguł programu Make](../build/commands-in-a-makefile.md)