---
title: IRowsetImpl::m_bReset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9aec38e3cf7e9a58c4fe99d06f35ae55cfdf81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102010"
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