---
title: CDynamicParameterAccessor::SetParamStatus | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
dev_langs: C++
helpviewer_keywords: SetParamStatus method
ms.assetid: 0c2271f6-457d-46ca-88b7-4590aadb20d7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b239000efa761ee30aa44fb8285fa96992e0b0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparamstatus"></a>CDynamicParameterAccessor::SetParamStatus
Ustawia stan określony parametr przechowywane w buforze.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      bool SetParamStatus(  
   DBORDINAL nParam,  
   DBSTATUS status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowana dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego kolejności w języku SQL lub procedurę składowaną wywołania. Zobacz [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *Stan*  
 [in] `DBSTATUS` Stan określony parametr. Aby uzyskać informacje dotyczące `DBSTATUS` wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*, lub Wyszukaj `DBSTATUS` w oledb.h.  
  
## <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)