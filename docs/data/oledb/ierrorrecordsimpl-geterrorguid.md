---
title: IErrorRecordsImpl::GetErrorGUID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
dev_langs:
- C++
helpviewer_keywords:
- GetErrorGUID method
ms.assetid: 42c00755-50e5-401a-8246-adef9de5ced2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a17529b9132a322cf1610baa1463d921c313e118
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ierrorrecordsimplgeterrorguid"></a>IErrorRecordsImpl::GetErrorGUID
Pobiera błąd identyfikatora GUID z rekord błędu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      REFGUID GetErrorGUID(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rCurError`  
 `ERRORINFO` Rekordów w **IErrorInfo** interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do identyfikatora GUID dla błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IErrorRecordsImpl, klasa](../../data/oledb/ierrorrecordsimpl-class.md)