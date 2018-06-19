---
title: CDynamicAccessor::GetOrdinal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
dev_langs:
- C++
helpviewer_keywords:
- GetOrdinal method
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e935340265d0239240ce47169aecb4f3210a106f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094400"
---
# <a name="cdynamicaccessorgetordinal"></a>CDynamicAccessor::GetOrdinal
Pobiera numer kolumny otrzymuje nazwę kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      bool GetOrdinal(const CHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  

bool GetOrdinal(const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pColumnName`  
 [in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.  
  
 *pOrdinal*  
 [out] Wskaźnik do liczby kolumn.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli zostanie znaleziony kolumnę o określonej nazwie. W przeciwnym razie ta funkcja zwraca **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)