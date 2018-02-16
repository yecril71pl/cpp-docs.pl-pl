---
title: "Cdynamicstringaccessora — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessorA
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0514dd3cd87788a6512b18d0aa3f2a5b7a842317
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA — Klasa
Umożliwia dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (struktury).  
  
## <a name="syntax"></a>Składnia

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## <a name="remarks"></a>Uwagi  
 Oba żądania, czy dostawca pobrać wszystkie dane uzyskiwane ze źródła danych jako ciągu dane, ale `CDynamicStringAccessor` dane ciągu ANSI żądania.  
  
 `CDynamicStringAccessorA` dziedziczy **GetString** i `SetString` z `CDynamicStringAccessor`. Jeśli używasz tych metod w `CDynamicStringAccessorA` obiektu ***BaseType*** jest **CHAR**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor — klasa](../../data/oledb/caccessor-class.md)   
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)