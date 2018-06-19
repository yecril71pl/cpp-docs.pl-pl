---
title: Klasa CSession | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs:
- C++
helpviewer_keywords:
- CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03c0bfec758bb663803b05b1f690816394f61239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097084"
---
# <a name="csession-class"></a>Klasa CSession
Reprezentuje sesję dostępu pojedynczej bazy danych.  
  
## <a name="syntax"></a>Składnia

```cpp
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