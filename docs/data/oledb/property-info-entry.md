---
title: PROPERTY_INFO_ENTRY | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a5db7ac8d5420f8daf5e55d2027aee90f1b682e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
Reprezentuje określoną właściwość w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
PROPERTY_INFO_ENTRY(  
dwPropID   
)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) identyfikatora GUID do identyfikowania właściwości ustawić wartość, która może być używane w połączeniu z właściwością.  
  
## <a name="remarks"></a>Uwagi  
 To makro ustawia wartości właściwości typu `DWORD` do wartości domyślnej zdefiniowanej w ATLDB. H. Aby ustawić właściwość na wartość wybrane, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Aby ustawić [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) i [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) dla właściwości w tym samym czasie, należy użyć [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)