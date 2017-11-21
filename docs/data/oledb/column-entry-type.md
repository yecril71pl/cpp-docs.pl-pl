---
title: COLUMN_ENTRY_TYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_ENTRY_TYPE
dev_langs: C++
helpviewer_keywords: COLUMN_ENTRY_TYPE macro
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 425f7e38002976d5510707768774f924f3627bc0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="columnentrytype"></a>COLUMN_ENTRY_TYPE
Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje `type` parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COLUMN_ENTRY_TYPE (  
nOrdinal  
,   
wType  
,   
data  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOrdinal`  
 [in] Numer kolumny.  
  
 `wType`  
 [in] Typ danych kolumny wpisu.  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 To makro jest specjalne wariant [column_entry —](../../data/oledb/column-entry.md) makra, która umożliwia określenie typu danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)