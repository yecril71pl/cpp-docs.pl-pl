---
title: CDBPropIDSet::CDBPropIDSet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class, constructor
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eb1aa5b832e8be0e90e34c32c9ad76a8c1c314f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090702"
---
# <a name="cdbpropidsetcdbpropidset"></a>CDBPropIDSet::CDBPropIDSet
Konstruktor. Inicjuje **rgProperties**, **cProperties**i (opcjonalnie) **guidPropertySet** pola [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Identyfikator GUID używany do inicjowania **guidPropertySet** pola.  
  
 *propidset*  
 [in] Inny `CDBPropIDSet` obiekt do tworzenia kopii.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdbpropidset — klasa](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)