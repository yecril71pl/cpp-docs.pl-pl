---
title: CEnumerator::Open | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1492208d75637a1a0e3eb1b959aac34a81043b07
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
Wiąże krótka nazwa dla typu wyliczeniowego, jeśli jeden jest określona, a następnie pobiera zestawu wierszy dla modułu wyliczającego, wywołując [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  


HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  


HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMoniker`  
 [in] Wskaźnik do krótka nazwa dla typu wyliczeniowego.  
  
 *pClsid*  
 [in] Wskaźnik do **CLSID** modułu wyliczającego.  
  
 `enumerator`  
 [in] Odwołanie do modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CEnumerator, klasa](../../data/oledb/cenumerator-class.md)