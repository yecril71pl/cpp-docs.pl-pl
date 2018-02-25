---
title: PROPERTY_INFO_ENTRY_VALUE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_VALUE
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8adb8fb0c2978bdf5886d47fa0ee33cba8f8fbe4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
Reprezentuje określoną właściwość w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) identyfikatora GUID do identyfikowania właściwości ustawić wartość, która może być używane w połączeniu z właściwością.  
  
 *value*  
 [in] Wartość właściwości typu `DWORD`.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą makra, możesz bezpośrednio określić wartość właściwości typu `DWORD`. Aby ustawić właściwości do wartości domyślnej zdefiniowanej w ATLDB. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić wartość flagi i opcje dla właściwości, należy użyć [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Przykład  
 See [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)