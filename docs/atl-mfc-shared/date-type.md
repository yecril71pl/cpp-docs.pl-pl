---
title: DATE — typ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aafed046fa5724442e30014aa5634542de0f4aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358130"
---
# <a name="date-type"></a>DATE — typ
**Data** typu jest implementowane za pomocą 8-bajtowa liczba zmiennoprzecinkowa. Liczba dni są reprezentowane przez zwiększa liczbę całkowitą, począwszy od 30 grudnia 1899, północy czasu zero. Wartości godziny są wyrażone jako wartość bezwzględną liczby ułamkową część liczby. W poniższej tabeli przedstawiono kilka dat wraz z ich **data** odpowiednik liczbowy typu:  
  
|Data i godzina|Reprezentacja wartości|  
|-------------------|--------------------|  
|30 grudnia 1899, północy|0.00|  
|1 stycznia 1900 północy|2.00|  
|4 stycznia 1900 północy|5.00|  
|4 stycznia 1900 godziny 6: 00|5.25|  
|4 stycznia 1900 południe|5.50|  
|4 stycznia 1900 godzinie 9|5.875|  
  
 **Data** typu date, jak również `COleDateTime` klasy reprezentuje dat i godzin jako klasycznego wiersza numer. `COleDateTime` Klasa zawiera kilka metod do manipulowania wartości daty, łącznie z konwersji do i z innych popularnych formatów daty.  
  
 Podczas pracy z tych formatów daty i godziny w automatyzacji należy zauważyć następujące kwestie:  
  
-   Daty są określane w czasie lokalnym; należy wykonać synchronizację ręcznie podczas pracy z daty w różnych strefach czasowych.  
  
-   Typy Data bez uwzględnienia czasu letniego.  
  
-   Oś czasu Data staje się nieciągłego dla wartości daty mniejszą od 0 (przed 30 1899 grudnia). Jest to spowodowane część liczby całkowitej wartość daty jest traktowana jako podpisany, gdy część ułamkowa jest traktowany jako bez znaku. Innymi słowy liczbę całkowitą część wartości typu date może być dodatnie lub ujemne, gdy część ułamkowa wartości typu date zawsze jest dodawany do ogólnego logicznej daty. W poniższej tabeli przedstawiono kilka przykładów:  
  
|Data i godzina|Reprezentacja wartości|  
|-------------------|--------------------|  
|27 grudnia 1899, północy|-3.00|  
|28 grudnia 1899, południe|-2.50|  
|28 grudnia 1899, północy|-2.00|  
|29 grudnia 1899, północy|-1.00|  
|30 grudnia 1899, 18: 00|-0.75|  
|30 grudnia 1899, południe|-0.50|  
|30 grudnia 1899, godziny 6: 00|-0.25|  
|30 grudnia 1899, północy|0.00|  
|30 grudnia 1899, godziny 6: 00|0.25|  
|30 grudnia 1899, południe|0.50|  
|30 grudnia 1899, 18: 00|0.75|  
|31 grudnia 1899, północy|1.00|  
|1 stycznia 1900 północy|2.00|  
|1 stycznia 1900 południe|2.50|  
|2 stycznia 1900 północy|3.00|  
  
> [!CAUTION]
>  Należy pamiętać, że ponieważ 6:00:00 zawsze jest reprezentowany przez wartość ułamkową 0,25 niezależnie od tego, czy (po 30 grudnia 1899) liczbę całkowitą przedstawiającą dzień jest dodatnią lub ujemną (przed 30 grudnia 1899), prosty przestawne porównanie punktu błędnego posortować wszelkie **data** reprezentujący 6:00:00 w dniu starszych niż 12/30/1899 *później* niż **data** reprezentujący 7:00 AM tego samego dnia.  
  
 Więcej informacji na temat problemów związanych z **data** i `COleDateTime` typów można znaleźć w [klasy COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) i [daty i godziny: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime, klasa](../atl-mfc-shared/reference/coledatetime-class.md)

