---
title: Pliki dostawcy generowane przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 0638680482546f56f26b70660ab43bd9848438a3
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707476"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

**Kreator biblioteki ATL OLE DB Provider** generuje następujące pliki. Poniższe tematy Użyj krótkiej nazwy *niestandardowe*, ale dokładnie zależy od wyboru dokonanego podczas tworzenia dostawcy.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Custom*RS.cpp|Zawiera polecenia Pomocnika `Execute` metody i mapy kolumny dostawcy.|
|*Niestandardowe*DS.h|Implementuje obiektu źródła danych. Ten plik nagłówka zawiera map właściwości dla właściwości źródła danych.|
|*Niestandardowe*RS.h|Implementuje obiektów polecenia i zestawu wierszy. Ten plik nagłówka zawiera map właściwości dla zestawu wierszy i polecenie Właściwości.|
|*Niestandardowe*Sess.h|Implementuje obiektu sesji. Ten plik nagłówka zawiera map właściwości dla właściwości sesji.|
|*Niestandardowe*.rgs|Zawiera zarejestrowane obiekty wygenerowane przez **OLE DB Provider kreatora**.|

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
