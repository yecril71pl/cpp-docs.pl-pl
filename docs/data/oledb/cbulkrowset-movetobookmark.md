---
title: CBulkRowset::MoveToBookmark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ec5c21c11fc7a733b64ce97863e7fc4bfa583e6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
Pobiera oznaczony przez zakładki lub wiersza od określonego przesunięcia wiersza (`lSkip`) z tej zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `bookmark`  
 [in] Zakładki oznaczenie lokalizacji, z którego mają być pobierane dane.  
  
 `lSkip`  
 [in] Liczbę wierszy z zakładkę do wiersza docelowego. Jeśli `lSkip` wynosi zero, pierwszy wiersz pobranych jest zakładką wiersza. Jeśli `lSkip` 1, pierwszy wiersz pobranych jest wiersz po wierszu zakładką. Jeśli `lSkip` wynosi -1, pierwszy wiersz pobranych jest wierszy przed wierszem zakładką.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zobacz [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CBulkRowset, klasa](../../data/oledb/cbulkrowset-class.md)