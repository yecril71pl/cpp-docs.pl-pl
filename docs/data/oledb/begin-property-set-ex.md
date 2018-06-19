---
title: BEGIN_PROPERTY_SET_EX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPERTY_SET_EX
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 239ee5810b0ebf46e01c9c97b01a36fdca4a1392
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093103"
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
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)