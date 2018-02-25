---
title: CRowsetImpl::NameFromDBID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 623eeca73ceaf29e0cecbe80b2a4a8b447adefdc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
Wyodrębnia ciągu z **DBID** i kopiuje go do `bstr` przekazany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pDBID*  
 [in] Wskaźnik do **DBID** z którego mają zostać wyodrębnione ciąg.  
  
 `bstr`  
 [in] A [CComBSTR](../../atl/reference/ccombstr-class.md) odwołania do skopiowania **DBID** ciągu.  
  
 `bIndex`  
 [in] **true** Jeśli indeks **DBID**; **false** Jeśli tabeli **DBID**.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`. W zależności od tego, czy **DBID** jest tabeli lub indeksu (wskazywane przez `bIndex`), metoda będzie zwracany albo **DB_E_NOINDEX** lub **DB_E_NOTABLE**.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez `CRowsetImpl` implementacje [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) i [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowsetImpl, klasa](../../data/oledb/crowsetimpl-class.md)