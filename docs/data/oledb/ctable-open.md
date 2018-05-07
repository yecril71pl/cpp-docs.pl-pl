---
title: CTable::Open | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca271d8a88035151e6845db6b7cb9423c71c73ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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