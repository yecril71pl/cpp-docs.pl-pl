---
title: Pliki dostawcy generowane przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: de5c9056402cb1db25240772eb3c592523daafae
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525321"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora

::: moniker range="vs-2019"

Kreator ATL OLE DB Provider nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2017"

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
