---
title: Data i godzina
ms.date: 11/04/2016
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 32222b4a2a529716db2c414e0281e1b1ba16a0dd
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739167"
---
# <a name="date-and-time"></a>Data i godzina

Biblioteka MFC obsługuje kilka różnych sposobów pracy z datami i godzinami. Należą do nich następujące elementy:

- Klasy czasu ogólnego przeznaczenia. [CTime](../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) klasy hermetyzacji większość funkcjonalności powiązane z biblioteką czasu standardu ANSI, która jest zadeklarowana w czasie. H.

- Obsługa zegara systemowego. Za pomocą MFC w wersji 3.0, dodano obsługę `CTime` dla Win32 `SYSTEMTIME` i `FILETIME` typy danych.

- Obsługa automatyzacji [DATE — typ danych](../atl-mfc-shared/date-type.md). Data obsługuje daty, godziny i wartości daty/godziny. [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) i [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) klasy hermetyzacji tej funkcji. Działają one z [COleVariant](../mfc/reference/colevariant-class.md) klasy przy użyciu obsługi automatyzacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Data i godzina: Obsługa SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Data i godzina: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)

- [Data i godzina: Obsługa bazy danych](../atl-mfc-shared/date-and-time-database-support.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
