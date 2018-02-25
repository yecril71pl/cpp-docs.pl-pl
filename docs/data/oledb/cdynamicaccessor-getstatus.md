---
title: CDynamicAccessor::GetStatus | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: 8f1aba69-5c2c-4ca7-ad84-7b4b27995eb8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: db78ecf633e3f69e24f1684949bddc0e0c21ce2c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorgetstatus"></a>CDynamicAccessor::GetStatus
Pobiera stan określonej kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```
bool GetStatus(DBORDINAL nColumn,   
  DBSTATUS* pStatus) const throw();  

bool GetStatus(const CHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const WCHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
 `pColumnName`  
 [in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.  
  
 `pStatus`  
 [out] Wskaźnik do zmiennej zawierający stan kolumny. Zobacz [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli zostanie znaleziony określonej kolumny. W przeciwnym razie ta funkcja zwraca **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)