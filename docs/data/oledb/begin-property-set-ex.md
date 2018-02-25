---
title: BEGIN_PROPERTY_SET_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_PROPERTY_SET_EX
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46f20308e037942ef3259d930fa89a3e08dca93d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="beginpropertysetex"></a>BEGIN_PROPERTY_SET_EX
Znaczniki ustawione na początku właściwości we właściwości ustaw mapy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid  
, flags )  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Właściwość identyfikatora GUID.  
  
 `flags`  
 [in] **UPROPSET_HIDDEN** dla wszystkie zestawy właściwość nie ma zostać udostępniona, lub **UPROPSET_PASSTHROUGH** dla dostawcy udostępnianie właściwości zdefiniowane poza zakresem dostawcy.  
  
## <a name="example"></a>Przykład  
 See [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)