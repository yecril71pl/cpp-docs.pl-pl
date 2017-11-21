---
title: PROPERTY_INFO_ENTRY_EX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY_EX
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY_EX macro
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 61842dc963ae442d23f802c1fd64c037f4a882e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentryex"></a>PROPERTY_INFO_ENTRY_EX
Reprezentuje określoną właściwość w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
PROPERTY_INFO_ENTRY_EX(  
dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) identyfikatora GUID do identyfikowania właściwości ustawić wartość, która może być używane w połączeniu z właściwością.  
  
 *VT*  
 [in] [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) tego wpisu właściwości.  
  
 `dwFlags`  
 [in] A [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) wartości opisujące ten wpis właściwości.  
  
 *wartość*  
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