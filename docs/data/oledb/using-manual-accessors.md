---
title: "Korzystanie z ręcznych metod dostępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7d6bd8f0228103e4899e6bc24f6d67af0f3fdb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="using-manual-accessors"></a>Korzystanie z ręcznych metod dostępu
Istnieją cztery czynności wykonywane podczas obsługi nieznane polecenie:  
  
-   Określanie parametrów  
  
-   Uruchom polecenie  
  
-   Określić kolumny wyjściowe  
  
-   Czy istnieją wiele zestawów wierszy zwracanych  
  
 Aby to zrobić z szablonami konsumentów DB OLE, należy użyć `CManualAccessor` klasy i wykonaj następujące czynności:  
  
1.  Otwórz `CCommand` obiekt z `CManualAccessor` jako parametr szablonu.  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Zapytanie sesji dla **IDBSchemaRowset** interfejsu i użyć zestawu wierszy parametry procedury. Jeśli **IDBSchemaRowset** interfejs nie jest dostępny, zapytanie `ICommandWithParameters` interfejsu. Wywołanie `GetParameterInfo` informacji. Jeśli żaden interfejs nie jest dostępny, można założyć, że nie ma żadnych parametrów.  
  
3.  Dla każdego parametru wywołania `AddParameterEntry` Aby dodać parametry i ustaw dla nich.  
  
4.  Otwórz zestaw wierszy, ale ustaw dla parametru wiązania **false**.  
  
5.  Wywołanie `GetColumnInfo` można pobrać kolumn wyjściowych. Użyj `AddBindEntry` można dodać kolumny wyjściowej do powiązania.  
  
6.  Wywołanie `GetNextResult` do ustalenia, czy zestawy więcej wierszy są dostępne. Powtórz kroki od 2 do 5.  
  
 Na przykład ręczne metody dostępu Zobacz **CDBListView::CallProcedure** w [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)