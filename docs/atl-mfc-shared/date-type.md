---
title: Typ daty
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 5a6c1e1cca5b2cb978d6af4208377db1a2926357
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502182"
---
# <a name="date-type"></a>Typ daty

Typ daty jest implementowany przy użyciu 8-bajtowej liczby zmiennoprzecinkowej. Dni są reprezentowane przez całkowitą liczbę przyrostów, zaczynając od 30 grudnia 1899, północy jako czas 0. Wartości godzinowe są wyrażane jako wartość bezwzględna części ułamkowej liczby. W poniższej tabeli przedstawiono kilka dat wraz z ich typem daty równoważnej liczbie:

|Data i godzina|Reprezentowana|
|-------------------|--------------------|
|30 grudnia 1899, północy|0,00|
|1 stycznia 1900, północy|2,00|
|4 stycznia 1900, północ|5,00|
|4 stycznia 1900, rano|5,25|
|4 stycznia 1900, południe|5,50|
|4 stycznia 1900, 9 P.M.|5,875|

Typ daty, a także `COleDateTime` Klasa, reprezentuje daty i godziny jako klasyczny wiersz numeru. `COleDateTime`Klasa zawiera kilka metod manipulowania wartościami dat, w tym konwersji do i z innych typowych formatów daty.

Następujące punkty należy zauważyć podczas pracy z tymi formatami daty i godziny w usłudze Automation:

- Daty są określone w czasie lokalnym; synchronizację należy przeprowadzić ręcznie podczas pracy z datami w różnych strefach czasowych.

- Typy dat nie uwzględniają czasu letniego.

- Oś czasu zaczyna być nieciągła dla wartości daty mniejszej niż 0 (przed 30 grudnia 1899). Wynika to z faktu, że część wartości daty jest traktowana jako podpisana, a część ułamkowa jest traktowana jako niepodpisana. Innymi słowy, część liczbowa wartości daty może być dodatnia lub ujemna, podczas gdy część ułamkowa wartości daty jest zawsze dodawana do ogólnej daty logicznej. W poniższej tabeli przedstawiono kilka przykładów:

|Data i godzina|Reprezentowana|
|-------------------|--------------------|
|27 grudnia 1899, północy|-3,00|
|28 grudnia 1899, południe|-2,50|
|28 grudnia 1899, północy|-2,00|
|29 grudnia 1899, północy|-1,00|
|30 grudnia 1899, godz.|-0,75|
|30 grudnia 1899, południe|-0,50|
|30 grudnia 1899, 6:00|-0,25|
|30 grudnia 1899, północy|0,00|
|30 grudnia 1899, 6:00|0,25|
|30 grudnia 1899, południe|0,50|
|30 grudnia 1899, godz.|0,75|
|31 grudnia 1899, północy|1,00|
|1 stycznia 1900, północy|2,00|
|1 stycznia 1900, południe|2,50|
|2 stycznia 1900, północy|3,00|

> [!CAUTION]
> Należy zauważyć, że w przypadku, gdy 6:00 jest zawsze reprezentowane przez wartość ułamkową 0,25 bez względu na to, czy liczba całkowita reprezentująca dzień jest dodatnia (po 30 grudnia 1899) czy ujemna (przed 30 grudnia 1899), proste porównanie zmiennoprzecinkowe będzie błędnie sortować dowolną datę, która przedstawia 6:00, na dzień wcześniejszy *niż 12/30/1899, jak w* przypadku daty reprezentowanej na tym samym dniu.

Więcej informacji na temat problemów związanych z datą i `COleDateTime` typami można znaleźć w obszarze [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) and [Data i Time (Obsługa automatyzacji](./date-and-time.md)).

## <a name="see-also"></a>Zobacz też

[Data i godzina](../atl-mfc-shared/date-and-time.md)<br/>
[Klasa COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)
