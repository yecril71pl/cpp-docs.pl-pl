---
title: Klasa CSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs: C++
helpviewer_keywords: CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d8b6bb75d12b4ab96c3a44c74f4487eb8a70efc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csession-class"></a>Klasa CSession
Reprezentuje sesję dostępu pojedynczej bazy danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSession  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Przerwania](../../data/oledb/csession-abort.md)|Anuluje (kończy) transakcji.|  
|[Zamknij](../../data/oledb/csession-close.md)|Zamyka sesję.|  
|[Zatwierdź](../../data/oledb/csession-commit.md)|Zatwierdza transakcji.|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|Zwraca informacje dotyczące transakcji.|  
|[Otwórz](../../data/oledb/csession-open.md)|Zostanie otwarta nowa sesja dla obiekt źródła danych.|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|Rozpoczyna nową transakcję dla tej sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Co najmniej jednej sesji może być skojarzony z każdego połączenia dostawcy (źródła danych), która jest reprezentowana przez [CDataSource](../../data/oledb/cdatasource-class.md) obiektu. Aby utworzyć nową `CSession` dla `CDataSource`, wywołaj [CSession::Open](../../data/oledb/csession-open.md). Aby rozpocząć transakcji bazy danych, `CSession` zapewnia `StartTransaction` metody. Po rozpoczęciu transakcji można przekazać do niej przy użyciu **zatwierdzania** metody, lub Anuluj ją przy użyciu **przerwać** metody.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CatDB](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)