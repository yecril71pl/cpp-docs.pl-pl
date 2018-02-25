---
title: Interfejsy obiektu sesji | Dokumentacja firmy Microsoft
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
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 71ac196508fc5b5054015bdc161476b75af2a598
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="session-object-interfaces"></a>Interfejsy obiektu sesji
W poniższej tabeli przedstawiono interfejsów obowiązkowe i opcjonalne zdefiniowanych przez OLE DB dla obiekt sesji.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|Obowiązkowy|Tak|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|Obowiązkowy|Tak|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|Obowiązkowy|Tak|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Optional|Nie|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Optional|Nie|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Optional|Nie|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Optional|Nie|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Optional|Tak|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Optional|Tak|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Optional|Nie|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|Tak|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Optional|Nie|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Optional|Nie|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Optional|Nie|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Optional|Nie|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Optional|Nie|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Optional|Nie|  
|[ITransactionObject](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Optional|Nie|  
  
 Obiekt sesji tworzy obiektu zestawu wierszy. Jeśli dostawca obsługuje poleceń, sesja również tworzy obiekt polecenia (`CCommand`, implementowanie OLE DB **TCommand**). Obiekt polecenia implementuje `ICommand` interfejsu i używa `ICommand::Execute` metodę można wykonać polecenia w zestawie wierszy, jak pokazano na poniższej ilustracji.  
  
 ![Diagram koncepcyjny dostawcy](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)