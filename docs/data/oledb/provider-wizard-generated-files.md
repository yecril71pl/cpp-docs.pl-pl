---
title: Pliki dostawcy generowane przez kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 26e20e0417e2253158930a8d3d055171fe767001
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108407"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora

ATL OLE DB Provider kreatora generuje następujące pliki. Poniższe tematy użyć krótkiej nazwy "MyProvider", ale dokładnie zależą od wybranego typu wprowadzone w czasie tworzenia dostawcy usługi.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|MyProviderRS.cpp|Zawiera polecenia Pomocnika `Execute` metody i mapy kolumny dostawcy.|  
|MyProviderDS.h|Implementuje obiektu źródła danych. Ten plik nagłówka zawiera map właściwości dla właściwości źródła danych.|  
|MyProviderRS.h|Implementuje obiektów polecenia i zestawu wierszy. Ten plik nagłówka zawiera map właściwości dla zestawu wierszy i polecenie Właściwości.|  
|MyProviderSess.h|Implementuje obiektu sesji. Ten plik nagłówka zawiera map właściwości dla właściwości sesji.|  
|MyProvider.rgs|Zawiera zarejestrowane obiekty generowane przez kreatora dostawcy bazy danych OLE.|  
  
## <a name="see-also"></a>Zobacz też  

[Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)