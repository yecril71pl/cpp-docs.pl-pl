---
title: Pliki dostawcy generowane przez kreatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27fb95e5dc1c417d3dfb03217463a8ef683f3710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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