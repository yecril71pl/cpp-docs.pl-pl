---
title: CDBPropIDSet::SetGUID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87878b6cc7ae38f2c9ffcf597a56ab020d8e9c8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090329"
---
# <a name="cdbpropidsetsetguid"></a>CDBPropIDSet::SetGUID
Ustawia w polu identyfikatora GUID **DBPROPIDSET** struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Identyfikator GUID używany do ustawiania **guidPropertySet** pole [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktury.  
  
## <a name="remarks"></a>Uwagi  
 W tym polu można wprowadzić przez [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) również. Wywołanie tej funkcji, jeśli używasz domyślnego konstruktora dla tej klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDBPropIDSet, klasa](../../data/oledb/cdbpropidset-class.md)