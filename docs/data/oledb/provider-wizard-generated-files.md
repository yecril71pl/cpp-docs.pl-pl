---
title: Pliki dostawcy generowane przez kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9bc7c85dccdfe095412450d5020fc8a6b42d516
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076974"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora

ATL OLE DB Provider kreatora generuje następujące pliki. Poniższe tematy Użyj krótkiej nazwy *niestandardowe*, ale dokładnie zależy od wyboru dokonanego podczas tworzenia dostawcy.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Niestandardowe*RS.cpp|Zawiera polecenia Pomocnika `Execute` metody i mapy kolumny dostawcy.|
|*Niestandardowe*DS.h|Implementuje obiektu źródła danych. Ten plik nagłówka zawiera map właściwości dla właściwości źródła danych.|
|*Niestandardowe*RS.h|Implementuje obiektów polecenia i zestawu wierszy. Ten plik nagłówka zawiera map właściwości dla zestawu wierszy i polecenie Właściwości.|
|*Niestandardowe*Sess.h|Implementuje obiektu sesji. Ten plik nagłówka zawiera map właściwości dla właściwości sesji.|
|*Niestandardowe*.rgs|Zawiera zarejestrowane obiekty generowane przez kreatora dostawcy bazy danych OLE.|

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)