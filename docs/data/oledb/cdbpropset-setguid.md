---
title: CDBPropSet::SetGUID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs: C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca1d8b4b6ee46f7debb52a6ebd0bbfbeded1fede
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
Ustawia **guidPropertySet** w **DBPROPSET** struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Identyfikator GUID używany do ustawiania **guidPropertySet** pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury.  
  
## <a name="remarks"></a>Uwagi  
 W tym polu można wprowadzić przez [Konstruktor](../../data/oledb/cdbpropset-cdbpropset.md) również.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdbpropset — klasa](../../data/oledb/cdbpropset-class.md)