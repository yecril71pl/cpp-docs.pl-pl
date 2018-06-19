---
title: PROVIDER_COLUMN_ENTRY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY macro
ms.assetid: 7921cfc1-aa9c-493e-8fc4-9d4294cafe72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 374e46d37e412c7b631e9f5d1361caeb77f2022c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106781"
---
# <a name="providercolumnentry"></a>PROVIDER_COLUMN_ENTRY
Przedstawia kolumnę określonych obsługiwane przez dostawcę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY (name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 `ordinal`  
 [in] Numer kolumny. Jeśli kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 `member`  
 [in] Zmiennej członkowskiej w `dataClass` odpowiadające kolumnie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)