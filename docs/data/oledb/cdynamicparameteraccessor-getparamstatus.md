---
title: CDynamicParameterAccessor::GetParamStatus | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
dev_langs:
- C++
helpviewer_keywords:
- GetParamStatus method
ms.assetid: 9300225a-616c-4a7d-82d0-8c2ecd4d8185
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89c4e97617018645dfea347f9a5f5e6155506f7b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicparameteraccessorgetparamstatus"></a>CDynamicParameterAccessor::GetParamStatus
Pobiera stan określony parametr przechowywane w buforze.  
  
## <a name="syntax"></a>Składnia  
  
```
bool GetParamStatus(DBORDINAL nParam,  
  DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowana dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego kolejności w języku SQL lub procedurę składowaną wywołania. Zobacz [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 `pStatus`  
 [out] Wskaźnik do zmiennej zawierający `DBSTATUS` stan określony parametr. Aby uzyskać informacje dotyczące `DBSTATUS` wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*, lub Wyszukaj `DBSTATUS` w oledb.h.  
  
## <a name="remarks"></a>Uwagi  
 Zwraca zastąpienie pierwszy **true** w przypadku powodzenia lub **false** w przypadku awarii. Drugi zastąpić punktów pamięci zawierający stan określony parametr.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)