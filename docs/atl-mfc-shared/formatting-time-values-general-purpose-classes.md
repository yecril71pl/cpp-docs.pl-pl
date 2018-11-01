---
title: 'Formatowanie wartości czasu: Klasy ogólnego przeznaczenia'
ms.date: 11/04/2016
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
ms.openlocfilehash: 48290adbc3e0e7f3cbe9a5a8e0569a5b61833e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478666"
---
# <a name="formatting-time-values-general-purpose-classes"></a>Formatowanie wartości czasu: Klasy ogólnego przeznaczenia

Poniższa procedura pokazuje sposób formatowania wartości typu time.

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>Format ciągu reprezentującego czas lub czas, który upłynął

Użyj `Format` funkcja elementu członkowskiego albo [CTime](../atl-mfc-shared/reference/ctime-class.md) lub [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) klasy do tworzenia znaku ciągu reprezentujący czas lub czas, który upłynął, jak pokazano na poniższym przykładzie.

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Ogólne Data i godzina programowania w MFC](../atl-mfc-shared/date-and-time.md)

- [Praca z SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Obsługa automatyzacji daty i godziny programowania](../atl-mfc-shared/date-and-time-automation-support.md)

