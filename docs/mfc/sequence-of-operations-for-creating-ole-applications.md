---
title: Sekwencja operacji przy tworzeniu aplikacji OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b281cbeb4670af0efd232152010fdc90795af103
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437352"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Sekwencja operacji przy tworzeniu aplikacji OLE

W poniższej tabeli przedstawiono usługi roli i roli w ramach tworzenia OLE, łączenie i osadzanie aplikacji. Reprezentują one dostępnymi zamiast sekwencję kroków do wykonania.

### <a name="creating-ole-applications"></a>Tworzeniu aplikacji OLE

|Zadanie|Możesz zrobić|Struktura jest|
|----------|------------|------------------------|
|Tworzenie składnika COM.|Uruchom Kreatora aplikacji MFC. Wybierz **pełny serwer** lub **miniserwera** w **Obsługa dokumentów złożonych** kartę.|Struktura generuje szkielet aplikacji dzięki możliwości składnika COM. Wszystkie możliwości COM mogą zostać przeniesione do istniejących aplikacji przy użyciu tylko niewielkich modyfikacji.|
|Tworzenie aplikacji kontenera od podstaw.|Uruchom Kreatora aplikacji MFC. Wybierz **kontenera** w **Obsługa dokumentów złożonych** kartę. Za pomocą widoku klas, przejdź do edytora kodu źródłowego. Wprowadź kod dla funkcji obsługi COM.|Struktura generuje szkielet aplikacji, która może wstawiać obiektów COM, utworzone przez aplikacje (serwer) składnika COM.|
|Utwórz aplikację, która obsługuje automatyzację od podstaw.|Uruchom Kreatora aplikacji MFC. Wybierz **automatyzacji** z **funkcje zaawansowane** kartę. Użyj widoku klas do udostępnienia, metody i właściwości w aplikacji automatyzacji.|Struktura generuje szkielet aplikacji, które mogą być aktywowany zautomatyzowane przez inne aplikacje.|

## <a name="see-also"></a>Zobacz też

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Sekwencja operacji przy tworzeniu kontrolek ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)

