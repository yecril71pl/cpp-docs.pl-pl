---
title: CHAIN_PROPERTY_SET | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5a80f6c834c3359d3a4be40b892ff4e5600e9e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
To makro powiązany ze sobą grupy właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *ChainClass*  
 [in] Nazwa klasy do właściwości łańcucha. To jest klasa generowane przez kreatora Projekt ATL, która zawiera już mapy (na przykład sesji, polecenie lub dane obiektu klasę źródłową).  
  
## <a name="remarks"></a>Uwagi  
 Możesz łańcucha zestaw właściwości z innej klasy do własnej klasy, a następnie uzyskać dostęp do właściwości bezpośrednio z klasy.  
  
> [!CAUTION]
>  Używanie tego makra oszczędnie. Nieprawidłowe użycie może spowodować konsumenta niepowodzenie testów zgodności z OLE DB.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)