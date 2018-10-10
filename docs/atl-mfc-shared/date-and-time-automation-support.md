---
title: 'Data i godzina: Obsługa automatyzacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ce0acc7eb90e534e1e66882f5a4a6a88b1eb782
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890182"
---
# <a name="date-and-time-automation-support"></a>Data i godzina: Obsługa automatyzacji

W tym artykule opisano sposób korzystać z usług biblioteki klas, które są związane z zarządzaniem daty i godziny. Procedury opisane obejmują:

- [Pobieranie bieżącego czasu](../atl-mfc-shared/current-time-automation-classes.md)

- [Obliczanie czasu, który upłynął](../atl-mfc-shared/elapsed-time-automation-classes.md)

- [Formatowanie daty/godziny reprezentację ciągu](../atl-mfc-shared/formatting-time-automation-classes.md)

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) klasy zapewnia sposób przedstawiania informacji daty i godziny. Zapewnia bardziej szczegółowy i większy zakres niż [CTime](../atl-mfc-shared/reference/ctime-class.md) klasy. [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) klasa reprezentuje czas, który upłynął, takich jak różnicę między dwoma `COleDateTime` obiektów.

`COleDateTime` i `COleDateTimeSpan` klasy są przeznaczone do użycia z `COleVariant` klasy używane w usłudze Automation. `COleDateTime` i `COleDateTimeSpan` są także przydatne w programowaniu bazy danych MFC, ale mogą być używane, gdy chcesz przekształcić wartości daty i godziny. Mimo że `COleDateTime` klasa ma większy zakres wartości i bardziej szczegółowy od `CTime` klasy, wymaga więcej pamięci masowej dla każdego obiektu niż `CTime`. Istnieją również pewne specjalne zagadnienia, pracując z podstawowego typu Data. Zobacz [typ daty](../atl-mfc-shared/date-type.md) dodatkowe szczegóły dotyczące implementacji daty.

`COleDateTime` obiekty może służyć do reprezentowania daty wypadające między 1 stycznia 100 r. a 31 grudnia 9999 r. `COleDateTime` wartości, przy użyciu przybliżoną rozdzielczość 1 milisekundy są zmiennoprzecinkowych obiektów. `COleDateTime` zależy od typu danych Data zdefiniowanego w dokumentacji MFC w obszarze [COleDateTime::operator data](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). Rzeczywiste wdrożenie Data wykracza poza tymi granicami. `COleDateTime` Implementacji nakłada tych granic w celu ułatwienia pracy z tej klasy.

`COleDateTime` nie obsługuje daty juliańskim. Kalendarz gregoriański zakłada, że rozszerzenie w czasie, 1 stycznia 100.

`COleDateTime` ignoruje czasu letniego (DST). Poniższy przykład kodu porównuje obliczanie przedział czasu, przecinającym Data przełączenie czasu letniego na dwa sposoby: ją przy użyciu CRT i inne przy użyciu `COleDateTime`. Czas letni przełącza, w większości ustawień regionalnych, drugi tydzień w kwietniu i innych w październiku.

Pierwsza metoda ustawia dwa `CTime` obiektów *godziny1* i *time2*, kwietnia 5 i 6 kwietnia odpowiednio przy użyciu standardowych struktury typu C `tm` i `time_t`. Ten kod wyświetla *godziny1* i *time2* i przedział czasu między nimi.

Druga metoda tworzy dwa `COleDateTime` obiektów `oletime1` i `oletime2`i ustawia je na tej samej daty jako *godziny1* i *time2*. Wyświetla `oletime1` i `oletime2` i przedział czasu między nimi.

CRT poprawnie oblicza różnicę 23 godzin. `COleDateTimeSpan` oblicza różnicę 24 godzin.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Data i godzina](../atl-mfc-shared/date-and-time.md)
