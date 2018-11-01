---
title: Pliki dostawcy generowane przez kreatora
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: c93618ebe9d3140864c2c47867ea970777c208b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580937"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora

**Kreator biblioteki ATL OLE DB Provider** generuje następujące pliki. Poniższe tematy Użyj krótkiej nazwy *niestandardowe*, ale dokładnie zależy od wyboru dokonanego podczas tworzenia dostawcy.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Niestandardowe*RS.cpp|Zawiera polecenia Pomocnika `Execute` metody i mapy kolumny dostawcy.|
|*Niestandardowe*DS.h|Implementuje obiektu źródła danych. Ten plik nagłówka zawiera map właściwości dla właściwości źródła danych.|
|*Niestandardowe*RS.h|Implementuje obiektów polecenia i zestawu wierszy. Ten plik nagłówka zawiera map właściwości dla zestawu wierszy i polecenie Właściwości.|
|*Niestandardowe*Sess.h|Implementuje obiektu sesji. Ten plik nagłówka zawiera map właściwości dla właściwości sesji.|
|*Niestandardowe*.rgs|Zawiera zarejestrowane obiekty wygenerowane przez **OLE DB Provider kreatora**.|

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
