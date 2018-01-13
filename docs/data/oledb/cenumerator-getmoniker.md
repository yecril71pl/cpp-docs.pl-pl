---
title: CEnumerator::GetMoniker | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
dev_langs: C++
helpviewer_keywords: GetMoniker method
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 41be8a27635d485ac4e2748df05211db7ff1c283
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cenumeratorgetmoniker"></a>CEnumerator::GetMoniker
Analizuje nazwę wyświetlaną na Wyodrębnij składnik ciąg, który może zostać przekonwertowany do krótkiej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetMoniker(   
   LPMONIKER* ppMoniker    
) const throw( );  
HRESULT GetMoniker(   
   LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *ppMoniker*  
 [out] Moniker przeanalizować Nazwa wyświetlana nadawcy ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) bieżącego wiersza.  
  
 *lpszDisplayName*  
 [in] Nazwa wyświetlana, można przeanalizować.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CEnumerator, klasa](../../data/oledb/cenumerator-class.md)