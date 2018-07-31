---
title: Interfejsy obiektu sesji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 01d08fb35a1e954aad07153f63ad3ed34282570d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337849"
---
# <a name="session-object-interfaces"></a>Interfejsy obiektu sesji
W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu sesji.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx)|Obowiązkowy|Tak|  
|[IOpenRowset](https://msdn.microsoft.com/library/ms716946.aspx)|Obowiązkowy|Tak|  
|[ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx)|Obowiązkowy|Tak|  
|[IAlterIndex](https://msdn.microsoft.com/library/ms714943.aspx)|Optional|Nie|  
|[IAlterTable](https://msdn.microsoft.com/library/ms719764.aspx)|Optional|Nie|  
|[IBindResource](https://msdn.microsoft.com/library/ms714936.aspx)|Optional|Nie|  
|[ICreateRow](https://msdn.microsoft.com/library/ms716832.aspx)|Optional|Nie|  
|[IDBCreateCommand](https://msdn.microsoft.com/library/ms711625.aspx)|Optional|Tak|  
|[IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx)|Optional|Tak|  
|[IIndexDefinition](https://msdn.microsoft.com/library/ms711593.aspx)|Optional|Nie|  
|[Interfejs ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Optional|Tak|  
|[ITableCreation](https://msdn.microsoft.com/library/ms713639.aspx)|Optional|Nie|  
|[ITableDefinition](https://msdn.microsoft.com/library/ms714277.aspx)|Optional|Nie|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/library/ms720947.aspx)|Optional|Nie|  
|[Metody ITransaction](https://msdn.microsoft.com/library/ms723053.aspx)|Optional|Nie|  
|[ITransactionJoin](https://msdn.microsoft.com/library/ms718071.aspx)|Optional|Nie|  
|[ITransactonLocal](https://msdn.microsoft.com/library/ms714893.aspx)|Optional|Nie|  
|[ITransactionObject](https://msdn.microsoft.com/library/ms713659.aspx)|Optional|Nie|  
  
 Obiekt sesji tworzy się obiektu zestawu wierszy. Jeśli dostawca obsługuje poleceń, sesja wzrasta, powstaje obiekt polecenia (`CCommand`, implementowanie OLE DB `TCommand`). Obiekt polecenia implementuje `ICommand` interfejsu i używa `ICommand::Execute` metody do wykonywania poleceń w zestawie wierszy, jak pokazano na poniższej ilustracji.  
  
 ![Diagram koncepcyjny dostawcy](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)