---
title: IRowsetImpl::m_bReset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs:
- C++
helpviewer_keywords:
- m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ca38b0fa56f901d18e90d3305c92cc097452369
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
Flaga bitowa używany w celu określenia, czy pozycja kursora jest zdefiniowany w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klient wywołuje [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) ujemnymi `lOffset` lub *cRows* i `m_bReset` ma wartość true, `GetNextRows` przenosi koniec zestawu wierszy. Jeśli `m_bReset` jest FAŁSZ, użytkownik otrzymuje kodu błędu, zgodnie ze specyfikacją OLE DB. `m_bReset` Flaga jest ustawiona na **true** najpierw utworzenia zestawu wierszy i kiedy klient wywołuje [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Pobiera wartość **false** podczas wywoływania `GetNextRows`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)