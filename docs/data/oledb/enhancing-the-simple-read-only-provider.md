---
title: Udoskonalanie prostego dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ad1ccd39ff66e4c193364549f58c78c6b743af0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="enhancing-the-simple-read-only-provider"></a>Udoskonalanie prostego dostawcy tylko do odczytu
W tej sekcji przedstawiono sposób zwiększenia [prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) utworzony w poprzedniej sekcji. `IRowsetLocateImpl`Tworzy implementację `IRowsetLocate` interfejsu i dodaje obsługę zakładki dla Ciebie.  
  
 Jeśli masz dostawcy pracy można poprawić, aby aktualizacja dostawcy, obsługi transakcji, lub zwiększyć wydajność algorytmu pobieranie z wiersza. Większość dostawcy ulepszenia obejmują dodawanie interfejsu do istniejącego obiektu COM.  
  
 Przykład w następujących tematach zwiększa mechanizmu pobieranie z wiersza przez dodanie `IRowsetLocate` interfejsu do `CAgentRowset`. Tematy przedstawiają sposób do:  
  
-   [Wprowadź RMyProviderRowset dziedziczyć irowsetlocate —](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Dynamiczne określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/creating-a-simple-read-only-provider.md)