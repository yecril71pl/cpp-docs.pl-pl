---
title: PROPERTY_INFO_ENTRY_EX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_EX
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_EX macro
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 186c30584c5c5844614994700bf2a7958a73ce2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="propertyinfoentryex"></a>PROPERTY_INFO_ENTRY_EX
Reprezentuje określoną właściwość w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) identyfikatora GUID do identyfikowania właściwości ustawić wartość, która może być używane w połączeniu z właściwością.  
  
 *vt*  
 [in] [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) tego wpisu właściwości.  
  
 `dwFlags`  
 [in] A [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) wartości opisujące ten wpis właściwości.  
  
 *value*  
 [in] Wartość właściwości typu `DWORD`.  
  
 `options`  
 Albo **DBPROPOPTIONS_REQUIRED** lub **DBPROPOPTIONS_SETIFCHEAP**. Zazwyczaj dostawcy nie trzeba ustawić `options` ustawione przez klienta.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą makra, możesz bezpośrednio określić wartość właściwości typu `DWORD` oraz opcje i flagi. Wartość domyślna zdefiniowana w ATLDB jedynie ustawiania właściwości. H, użyj [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Aby ustawić właściwość na wartość wybranym bez ustawiania opcji lub flagi, użyj [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)