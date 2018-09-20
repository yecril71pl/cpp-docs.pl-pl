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
ms.openlocfilehash: fe80a16f0085e37feaf7c80611fa303f1d3bf1ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425772"
---
# <a name="date-type"></a>DATE — typ

Typ daty jest implementowany przy użyciu 8-bajtowa liczba zmiennoprzecinkowa. Dni są reprezentowane przez zwiększa liczbę całkowitą z zakresu, począwszy od 30 grudnia 1899, o północy czasu zero. Wartości godziny są wyrażone jako wartość bezwzględną liczby część ułamkową liczby. W poniższej tabeli przedstawiono kilka dat wraz z ich daty typ numeryczny ekwiwalent:

|Data i godzina|Reprezentacja|
|-------------------|--------------------|
|30 grudnia 1899, północy|0.00|
|1 stycznia 1900 r. północy|2.00|
|4 stycznia 1900 północy|5.00|
|4 stycznia 1900 godziny 6: 00|5.25|
|4 stycznia 1900 południe|5.50|
|4 stycznia 1900 r. o 9|5.875|

Typ daty daty, także `COleDateTime` klasy reprezentuje daty i godziny, jako klasyczny wiersz numer. `COleDateTime` Klasa zawiera kilka metody do manipulowania wartości daty, w tym konwersji do i z innych typowych formatów daty.

Podczas pracy z tych formatów daty i godziny w usłudze Automation, należy zauważyć następujące kwestie:

- Daty są określane w czasie lokalnym; należy przeprowadzić synchronizację ręcznie podczas pracy z datami w różnych strefach czasowych.

- Typy daty nie uwzględniają czasu letniego.

- Oś czasu daty staje się nieciągły dla wartości daty mniejszą od 0 (przed 30 grudnia 1899). Jest to spowodowane część liczby całkowitej wartość daty jest traktowany jako podpisany, podczas gdy część ułamkową jest traktowany jako nieoznaczony. Innymi słowy część liczby całkowitej wartości typu date może nastąpić dodatnie lub ujemne, część ułamkowa wartości typu date jest zawsze dodawany do wartości typu date ogólną logiczne. W poniższej tabeli przedstawiono kilka przykładów:

|Data i godzina|Reprezentacja|
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
|Do 31 grudnia 1899, północy|1.00|
|1 stycznia 1900 r. północy|2.00|
|1 stycznia 1900 południe|2.50|
|2 stycznia 1900 północy|3.00|

> [!CAUTION]
>  Należy pamiętać, że ponieważ 6:00 AM zawsze jest reprezentowany przez wartość ułamkowa 0,25 niezależnie od tego, czy (po 30 grudnia 1899) liczbę całkowitą przedstawiającą dzień jest dodatnia lub ujemna (przed 30 grudnia 1899), prosty zmiennoprzecinkowy porównania punktu błędnie posortować Dowolna data reprezentujący 6:00:00 w dniu starszych niż 12/30/1899 *później* niż wartość typu DATE reprezentującą 7:00:00 tego samego dnia.

Więcej informacji na temat problemów związanych z DATĄ i `COleDateTime` typów można znaleźć w obszarze [COleDateTime, klasa](../atl-mfc-shared/reference/coledatetime-class.md) i [Data i godzina: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Zobacz też

[Data i godzina](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime, klasa](../atl-mfc-shared/reference/coledatetime-class.md)

