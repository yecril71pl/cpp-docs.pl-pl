---
title: "Data i godzina: Obsługa automatyzacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a40a8fe49d9564714c328b657bc0d85d52ad84b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="date-and-time-automation-support"></a>Data i godzina: Obsługa automatyzacji
W tym artykule opisano, jak korzystać z usług biblioteki klasy związane z zarządzaniem daty i godziny. Procedury opisane obejmują:  
  
-   [Pobieranie bieżącej godziny](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [Obliczanie czasu, który upłynął](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [Formatowanie reprezentację ciągu daty i godziny](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) klasa umożliwia reprezentują informacji daty i godziny. Zapewnia bardziej szczegółowy i większego zakresu niż [ctime —](../atl-mfc-shared/reference/ctime-class.md) klasy. [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) klasa reprezentuje czas, który upłynął, takich jak różnicę między dwiema `COleDateTime` obiektów.  
  
 `COleDateTime` i `COleDateTimeSpan` klas są przeznaczone do użycia z `COleVariant` klasa używana w automatyzacji. `COleDateTime`i `COleDateTimeSpan` są także przydatne podczas programowania bazy danych MFC, ale może być używana, gdy należy modyfikować wartości daty i godziny. Mimo że `COleDateTime` klasa ma większego zakresu wartości i bardziej szczegółowy od `CTime` klasy, wymaga więcej pamięci masowej dla obiekt niż `CTime`. Istnieją również pewne specjalne kwestie podczas pracy z podstawową **data** typu. Zobacz [typu Data](../atl-mfc-shared/date-type.md) uzyskać więcej informacji dotyczących stosowania **data**.  
  
 `COleDateTime`obiekty może służyć do reprezentowania daty wypadające między 1 stycznia 100 r. a 31 grudnia 9999 r. `COleDateTime`obiekty są zmiennoprzecinkowych wartości punktu z przybliżoną rozdzielczość 1 milisekundy. `COleDateTime`jest oparta na **data** danych typu zdefiniowanego w dokumentacji MFC w obszarze [COleDateTime::operator data](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). Rzeczywistego wykonania **data** wykracza poza granice te. `COleDateTime` Implementacji nakłada tych granic w celu ułatwienia pracy przy użyciu klasy.  
  
 `COleDateTime`nie obsługuje dat juliański. Kalendarza gregoriańskiego zakłada, że rozszerzenie na czas 1 stycznia 100.  
  
 `COleDateTime`ignoruje czasu (DST). Poniższy przykład kodu porównuje dwie metody obliczania przecina Data przełączenie czasu letniego przedział czasu: jeden przy użyciu CRT i inne `COleDateTime`. Czas letni przełącza, większość ustawień regionalnych, w drugim tygodniu kwietnia, a trzeci w październiku.  
  
 Pierwsza metoda ustawia dwa `CTime` obiektów, *godziny1* i *time2*, kwietnia 5 i 6 kwietnia odpowiednio przy użyciu standardowych struktur typu C **tm** i `time_t`. Wyświetla kod *godziny1* i *time2* i przedział czasu między nimi.  
  
 Druga metoda tworzy dwa `COleDateTime` obiektów, `oletime1` i `oletime2`i ustawia je do tej samej dat jako *godziny1* i *time2*. Wyświetla `oletime1` i `oletime2` i przedział czasu między nimi.  
  
 CRT poprawnie oblicza różnicę 23 godz. `COleDateTimeSpan`oblicza różnicę 24 godzin.  
  
 Pamiętaj, że obejście tego problemu jest stosowane zbliża się koniec przykładzie Aby wyświetlić datę prawidłowo przy użyciu `COleDateTime::Format`. Zobacz artykuł bazy wiedzy Knowledge Base "Błąd: Format("%D") nie powiedzie się `COleDateTime` i `COleDateTimeSpan`" (Q167338).  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina](../atl-mfc-shared/date-and-time.md)

