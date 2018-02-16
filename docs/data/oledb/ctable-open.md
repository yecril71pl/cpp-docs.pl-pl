---
title: CTable::Open | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8f4e969e1ab8fd6e43a2a8c1d568974b41f3b692
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ctableopen"></a>CTable::Open
Otwiera tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [in] Sesja otwieraniu tabeli.  
  
 *wszTableName*  
 [in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciąg Unicode.  
  
 *szTableName*  
 [in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciągu ANSI.  
  
 *dbid*  
 [in] **DBID** tabeli, aby otworzyć.  
  
 *pPropSet*  
 [in] Wskaźnik do tablicy [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury zawierające właściwości i wartości, które można ustawić. Zobacz [zestawy właściwości i grup właściwości](https://msdn.microsoft.com/en-us/library/ms713696.aspx) w *OLE DB Podręcznik programisty* w systemie Windows SDK. Domyślna wartość NULL określa żadnych właściwości.  
  
 `ulPropSets`  
 [in] Liczba [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) przekazano struktury *pPropSet* argumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CTable, klasa](../../data/oledb/ctable-class.md)