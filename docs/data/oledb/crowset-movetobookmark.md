---
title: CRowset::MoveToBookmark | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9f638f928c9fee0383e5ed50cd4b3dd547ad4939
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
Pobiera oznaczony przez zakładki lub wiersza od określonego przesunięcia wiersza (`lSkip`) z tej zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,   
   LONG lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `bookmark`  
 [in] Zakładki oznaczenie lokalizacji, z którego mają być pobierane dane.  
  
 `lSkip`  
 [in] Liczbę wierszy z zakładkę do wiersza docelowego. Jeśli `lSkip` wynosi zero, pierwszy wiersz pobranych jest zakładką wiersza. Jeśli `lSkip` 1, pierwszy wiersz pobranych jest wiersz po wierszu zakładką. Jeśli `lSkip` wynosi -1, pierwszy wiersz pobranych jest wierszy przed wierszem zakładką.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs `IRowsetLocate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetLocate** do `VARIANT_TRUE` i ustaw **DBPROP_CANFETCHBACKWARDS** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenia zawierający zestaw wierszy.  
  
 Aby dowiedzieć się, jak korzystanie z zakładek użytkowników, zobacz [przy użyciu zakładki](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)