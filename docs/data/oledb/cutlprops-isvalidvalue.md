---
title: CUtlProps::IsValidValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd02ef7c27926b2be99ed900b82d53c77d8d6dd0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Używany do sprawdzania poprawności wartości przed ustawieniem właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iCurSet`  
 Indeks tablicy właściwości zestawu; zero, jeśli istnieje tylko jedna właściwość.  
  
 `pDBProp`  
 Identyfikator właściwości i nową wartość w [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`. Zwraca wartość domyślna wartość to `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wszystkie procedury walidacji, który ma zostać uruchomione na wartości, które chcesz użyć, aby ustawić właściwość, należy przesłonić tę funkcję. Na przykład można zweryfikować **DBPROP_AUTH_PASSWORD** na tabeli hasło, aby określić prawidłową wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CUtlProps, klasa](../../data/oledb/cutlprops-class.md)