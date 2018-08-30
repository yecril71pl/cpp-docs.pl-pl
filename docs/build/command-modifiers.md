---
title: Polecenie Modyfikatory | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c9e1d883e0c7a2b214842b096fdf697ffc7d0192
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221744"
---
# <a name="command-modifiers"></a>Modyfikatory poleceń
Można określić co najmniej jeden Modyfikatory poleceń poprzedzającego polecenia, opcjonalnie rozdzielonych spacjami lub karty. Podobnie jak w przypadku poleceń, można wcięcia modyfikatory.  
  
|Modyfikator|Cel|  
|--------------|-------------|  
|@*Polecenie*|Uniemożliwia wyświetlanie polecenia. Wyświetlanie za pomocą poleceń nie jest pomijane. Domyślnie NMAKE funkcją wszystkie wykonane polecenia. Umożliwia /S Pomiń wyświetlanie dla całego pliku reguł programu make; Użyj **. DYSKRETNEJ** Pomija wyświetlanie części pliku reguł programu make.|  
|**-**\[*Liczba*] *polecenia*|Wyłącza sprawdzanie błędów *polecenia*. Domyślnie NMAKE zatrzymuje, gdy polecenie zwróci kod zakończenia różny od zera. IF -*numer* jest używany, NMAKE zatrzymuje, jeśli kod zakończenia przekracza *numer*. Spacje lub tabulatory nie może występować między kreska i *numer.* Co najmniej jeden spacja lub tabulator musi znajdować się między `number` i *polecenia*. Użyj/i wyłączyć sprawdzanie błędów dotyczących całego pliku reguł programu make; Użyj **. Ignoruj** wyłączyć sprawdzanie część pliku reguł programu make.|  
|**\!** *Polecenie*|Wykonuje *polecenia* dla każdego pliku zależnego Jeśli *polecenia* używa <strong>$ \* \*</strong> (wszystkie pliki zależne w zależności) lub **$?** (wszystkie pliki zależne powstanie zależności z sygnaturą czasową nowszy niż element docelowy).|  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia w pliku reguł programu Make](../build/commands-in-a-makefile.md)