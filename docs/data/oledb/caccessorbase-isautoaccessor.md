---
title: CAccessorBase::IsAutoAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs:
- C++
helpviewer_keywords:
- IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 304727142b6a3afb293b33c01746743118fa3a64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="caccessorbaseisautoaccessor"></a>CAccessorBase::IsAutoAccessor
Zwraca wartość PRAWDA, jeśli dane są automatycznie pobierane dla metody dostępu podczas operacji przenoszenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [in] Numer przesunięcie zero metodzie dostępu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** autoaccessor po metodzie dostępu. W przeciwnym razie zwraca **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CAccessorBase, klasa](../../data/oledb/caccessorbase-class.md)