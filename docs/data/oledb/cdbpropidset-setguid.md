---
title: CDBPropIDSet::SetGUID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs: C++
helpviewer_keywords: SetGUID method
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d91cc0374474a38bd2caba66ab98003852195f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropidsetsetguid"></a>CDBPropIDSet::SetGUID
Ustawia w polu identyfikatora GUID **DBPROPIDSET** struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Identyfikator GUID używany do ustawiania **guidPropertySet** pole [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktury.  
  
## <a name="remarks"></a>Uwagi  
 W tym polu można wprowadzić przez [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) również. Wywołanie tej funkcji, jeśli używasz domyślnego konstruktora dla tej klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdbpropidset — klasa](../../data/oledb/cdbpropidset-class.md)