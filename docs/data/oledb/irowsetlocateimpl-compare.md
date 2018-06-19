---
title: IRowsetLocateImpl::Compare | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 208f912e92045daec36066e1dcc06fc38b5a8ed2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105286"
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
Porównuje dwa zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Jedną z zakładki może być standard zdefiniowane OLE DB [standardowe zakładki](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST**, **DBBMK_LAST**, lub **DBBMK_INVALID**). Wartość zwracana w `pComparison` wskazuje relację między dwiema zakładek:  
  
-   **DBCOMPARE_LT** (`cbBookmark1` przed `cbBookmark2`.)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1` jest równa `cbBookmark2`.)  
  
-   **DBCOMPARE_GT** (`cbBookmark1` po `cbBookmark2`.)  
  
-   **DBCOMPARE_NE** (zakładki są takie same i nie uporządkowanych).  
  
-   **DBCOMPARE_NOTCOMPARABLE** (nie można porównać zakładki.)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetLocateImpl, klasa](../../data/oledb/irowsetlocateimpl-class.md)