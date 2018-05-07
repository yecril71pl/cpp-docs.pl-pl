---
title: CHAIN_PROPERTY_SET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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