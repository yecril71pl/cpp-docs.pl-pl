---
title: CDynamicAccessor::GetBookmark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
dev_langs: C++
helpviewer_keywords: GetBookmark method
ms.assetid: 6d0a2970-0c62-4a34-bac7-149d8e990f81
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9c8f6a2567684ffb7c7faee62cdca501c53ba0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetbookmark"></a>CDynamicAccessor::GetBookmark
Pobiera zakładki dla bieżącego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetBookmark(   
   CBookmark< >* pBookmark    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBookmark`  
 [out] Wskaźnik do [CBookmark](../../data/oledb/cbookmark-class.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Należy ustawić **DBPROP_IRowsetLocate** do `VARIANT_TRUE` można pobrać zakładki.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)