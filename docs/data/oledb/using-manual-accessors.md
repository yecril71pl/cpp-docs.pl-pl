---
title: Korzystanie z ręcznych metod dostępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 236fd1809fa012262f3a98f0f1856f3bbff6b454
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340867"
---
# <a name="using-manual-accessors"></a>Korzystanie z ręcznych metod dostępu
Istnieją cztery czynności wykonywane podczas obsługi nieznane polecenie:  
  
-   Określanie parametrów  
  
-   Wykonaj polecenie  
  
-   Określić kolumny wyjściowe  
  
-   Czy istnieją wielu zwracane zestawy wierszy  
  
 Aby to zrobić z szablonami konsumentów DB OLE, należy użyć `CManualAccessor` klasy i wykonaj następujące czynności:  
  
1.  Otwórz `CCommand` obiekt z `CManualAccessor` jako parametr szablonu.  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Kwerendy sesji dla `IDBSchemaRowset` interfejs i użyć zestawu wierszy parametrów procedury. Jeśli `IDBSchemaRowset` interfejs nie jest dostępny, wykonanie kwerendy `ICommandWithParameters` interfejsu. Wywołaj `GetParameterInfo` informacji. Jeśli żadna interfejs jest dostępny, można założyć, że nie ma żadnych parametrów.  
  
3.  Dla każdego parametru wywołania `AddParameterEntry` Dodaj parametry i ich ustawiania.  
  
4.  Otwórz zestaw wierszy, ale wartość parametru powiązania **false**.  
  
5.  Wywołaj `GetColumnInfo` można pobrać kolumn wyjściowych. Użyj `AddBindEntry` można dodać kolumnę wyjściową do powiązania.  
  
6.  Wywołaj `GetNextResult` do określenia, czy więcej zestawów wierszy są dostępne. Powtórz kroki od 2 do 5.  
  
 Na przykład ręczne metody dostępu Zobacz `CDBListView::CallProcedure` w [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)