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
ms.openlocfilehash: ac23f06bf1ae697ecd627d493aa5902219488138
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106011"
---
# <a name="provider-wizard-generated-files"></a>Pliki dostawcy generowane przez kreatora
OLE DB Provider Kreator ATL generuje następujące pliki. Poniższe tematy używać krótką nazwę "MyProvider", ale nazwy plików są zależne od wybranej podczas tworzenia dostawcy.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|MyProviderRS.cpp|Zawiera polecenia Pomocnika `Execute` — metoda i dostawcy mapowania kolumn.|  
|MyProviderDS.h|Implementuje obiektu źródła danych. Ten plik nagłówka zawiera mapę właściwości dla właściwości źródła danych.|  
|MyProviderRS.h|Implementuje obiekt polecenia i zestawu wierszy. Ten plik nagłówka zawiera mapę właściwości dla zestawu wierszy i polecenie Właściwości.|  
|MyProviderSess.h|Implementuje obiektu session. Ten plik nagłówka zawiera mapę właściwości dla właściwości sesji.|  
|MyProvider.rgs|Zawiera obiekty zarejestrowanych generowane przez kreatora dostawcy bazy danych OLE.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)