---
title: IRowsetImpl::m_bReset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs: C++
helpviewer_keywords: m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4323d92398ea4d47410a2b5a3aad08972628634d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
Flaga bitowa używany w celu określenia, czy pozycja kursora jest zdefiniowany w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klient wywołuje [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) ujemnymi `lOffset` lub *cRows* i `m_bReset` ma wartość true, `GetNextRows` przenosi koniec zestawu wierszy. Jeśli `m_bReset` jest FAŁSZ, użytkownik otrzymuje kodu błędu, zgodnie ze specyfikacją OLE DB. `m_bReset` Flaga jest ustawiona na **true** najpierw utworzenia zestawu wierszy i kiedy klient wywołuje [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Pobiera wartość **false** podczas wywoływania `GetNextRows`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)