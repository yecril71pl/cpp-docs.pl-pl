---
title: CEnumerator::Open | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 04e6884b27f45ee86085c1b820376ed087ae68c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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