---
title: CDynamicParameterAccessor::CDynamicParameterAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
dev_langs: C++
helpviewer_keywords:
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
ms.assetid: a1cce5e4-dfb9-43a2-bfb8-0435c653674a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e08c26c7ba9d07c5e845aea3443c824498354b74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a>CDynamicParameterAccessor::CDynamicParameterAccessor
Konstruktor.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor( eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Określa sposób obsługi danych obiektów BLOB. Wartość domyślna to **DBBLOBHANDLING_DEFAULT**. Zobacz [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) opis **DBBLOBHANDLINGENUM** wartości.  
  
 `nBlobSize`  
 Maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych za pośrednictwem tej wartości są traktowane jako obiektu BLOB. Wartość domyślna to 8000. Zobacz [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) szczegółowe informacje.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) konstruktora, aby uzyskać więcej informacji na temat obsługi obiektów BLOB.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)