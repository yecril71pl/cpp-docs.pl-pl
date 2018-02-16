---
title: "Cdynamicstringaccessorw — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessorW
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4230451743144bdf85a875c3daa981f5ca30f9f6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW — Klasa
Umożliwia dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (struktury).  
  
## <a name="syntax"></a>Składnia

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>Uwagi  
 Oba żądania, czy dostawca pobrać wszystkie dane uzyskiwane ze źródła danych jako ciągu dane, ale `CDynamicStringAccessor` żąda danych ciąg Unicode.  
  
 `CDynamicStringAccessorW` dziedziczy **GetString** i `SetString` z `CDynamicStringAccessor`. Jeśli używasz tych metod w `CDynamicStringAccessorW` obiektu ***BaseType*** jest **WCHAR**.  
  
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