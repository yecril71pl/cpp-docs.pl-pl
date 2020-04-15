---
title: DATE, typ
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
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317917"
---
# <a name="date-type"></a>DATE, typ

Typ DATE jest implementowany przy użyciu 8-bajtowej liczby zmiennoprzecinkowej. Dni są reprezentowane przez przyrosty liczby 0,50, począwszy od 30 grudnia 1899 r., o północy jako czas zero. Wartości godzin są wyrażone jako wartość bezwzględna ułamkowej części liczby. W poniższej tabeli przedstawiono kilka dat wraz z ich odpowiednikiem liczbowym typu DATE:

|Data i godzina|Reprezentacja|
|-------------------|--------------------|
|30 grudnia 1899, północ|0,00|
|1 stycznia 1900, północ|2,00|
|4 stycznia 1900, północ|5,00|
|4 stycznia 1900 r., godz.|5.25|
|4 stycznia 1900, w południe|5.50|
|4 stycznia 1900, godz.|5.875|

Typ daty daty, `COleDateTime` a także klasa, reprezentuje daty i godziny jako klasyczny wiersz liczbowy. Klasa `COleDateTime` zawiera kilka metod manipulowania wartościami DATE, w tym konwersji do i z innych typowych formatów daty.

Podczas pracy z tymi formatami daty i godziny w automatyzacji należy zwrócić uwagę na następujące kwestie:

- Daty są określone w czasie lokalnym; synchronizacja musi być wykonywana ręcznie podczas pracy z datami w różnych strefach czasowych.

- Typy dat nie uwzględniają czasu letniego.

- Termin daty staje się nieciągliwy dla wartości daty mniejszej niż 0 (przed 30 grudnia 1899 r.). Dzieje się tak, ponieważ część całkowita wartości daty jest traktowana jako podpisana, podczas gdy część ułamkowa jest traktowana jako niepodpisana. Innymi słowy, część całkowita liczbowa wartości daty może być dodatnia lub ujemna, podczas gdy ułamkowa część wartości daty jest zawsze dodawana do ogólnej daty logicznej. W poniższej tabeli przedstawiono kilka przykładów:

|Data i godzina|Reprezentacja|
|-------------------|--------------------|
|27 grudnia 1899, północ|-3.00|
|28 grudnia 1899, południe|-2.50|
|28 grudnia 1899, północ|-2.00|
|29 grudnia 1899, północ|-1.00|
|30 grudnia 1899 r., godz.|-0.75|
|30 grudnia 1899, południe|-0.50|
|30 grudnia 1899 r., godz.|-0.25|
|30 grudnia 1899, północ|0,00|
|30 grudnia 1899 r., godz.|0,25|
|30 grudnia 1899, południe|0,50|
|30 grudnia 1899 r., godz.|0,75|
|31 grudnia 1899 r., o północy|1,00|
|1 stycznia 1900, północ|2,00|
|1 stycznia 1900, w południe|2.50|
|2 stycznia 1900, północ|3,00|

> [!CAUTION]
> Należy zauważyć, że ponieważ 6:00 AM jest zawsze reprezentowana przez wartość ułamkową 0,25, niezależnie od tego, czy liczba całkowita reprezentująca dzień jest dodatnia (po 30 grudnia, 1899) lub ujemny (przed 30 grudnia 1899 r.), proste porównanie zmiennoprzecinkowe błędnie posortowałoby każdą datę reprezentującą 6:00 RANO dzień wcześniej niż 30 grudnia 1899 r. *jako późniejszą* niż data 7:00 w tym samym dniu.

Więcej informacji na temat problemów `COleDateTime` związanych z datą i typami można znaleźć w obszarze [Klasa COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) oraz [Data i godzina: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Zobacz też

[Data i godzina](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime, klasa](../atl-mfc-shared/reference/coledatetime-class.md)
