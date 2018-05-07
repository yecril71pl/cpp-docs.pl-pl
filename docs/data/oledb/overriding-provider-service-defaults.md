---
title: Zastępowanie ustawień domyślnych usługi dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be802c1c3c6ba4b77d1418c9c620840e9ab10170
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-provider-service-defaults"></a>Zastępowanie ustawień domyślnych usługi dostawcy
Wartość rejestru dostawcy **OLEDB_SERVICES** jest zwracana wartość domyślną dla [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) właściwości inicjowania obiektu źródła danych.  
  
 Tak długo, jak istnieje wpis rejestru, obiektów dostawcy jest agregowana, użytkownika można zmienić ustawienia dla usług włączone przez ustawienie domyślnego dostawcy **DBPROP_INIT_OLEDBSERVICES** właściwości przed zainicjowaniem. Aby włączyć lub wyłączyć określonej usługi, użytkownik ogólnie pobiera bieżącą wartość **DBPROP_INIT_OLEDBSERVICES** właściwości, ustawia lub czyści dla określonej właściwości włączyć lub wyłączyć i resetuje właściwość. **DBPROP_INIT_OLEDBSERVICES** można ustawić bezpośrednio w bazie danych OLE DB lub w parametrach połączenia przekazany do ADO lub **IDataInitialize::GetDatasource**. W poniższej tabeli wymieniono odpowiednie wartości, aby włączyć lub wyłączyć poszczególne usługi.  
  
|Włączone usługi domyślne|Wartość właściwości DBPROP_INIT_OLEDBSERVICES|Wartość w parametrach połączenia|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Wszystkie usługi (ustawienie domyślne)|**DBPROPVAL_OS_ENABLEALL**|"Usług OLE DB = -1;"|  
|Wszystkie z wyjątkiem puli i AutoEnlistment|**DBPROPVAL_OS_ENABLEALL &AMP;**<br /><br /> **~ DBPROPVAL_OS_RESOURCEPOOLING &AMP;**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT**|"Usług OLE DB = -4;"|  
|Wszystkie z wyjątkiem kursora klienta|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|"Usług OLE DB = -5;"|  
|Wszystkie z wyjątkiem puli AutoEnlistment i kursora klienta|**DBPROPVAL_OS_ENABLEALL &AMP;**<br /><br /> **~ DBPROPVAL_OS_TXNENLISTMENT &AMP;**<br /><br /> **~DBPROPVAL_OS_CLIENTCURSOR**|"Usług OLE DB = -7;"|  
|Nie usługi|~**DBPROPVAL_OS_ENABLEALL**|"Usług OLE DB = 0;"|  
  
 Jeśli wpis rejestru nie istnieje dla dostawcy, menedżerów składników nie zostaną zagregowane obiektów dostawcy, a żadne usługi zostanie wywołany, nawet jeśli jawnie żądanej przez użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z puli zasobów](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [Jak używać konsumentów pule zasobów](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [Jak dostawców działał efektywnie z puli zasobów](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)