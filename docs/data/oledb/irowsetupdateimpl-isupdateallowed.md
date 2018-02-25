---
title: IRowsetUpdateImpl::IsUpdateAllowed | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 13c74046748e64686c44c1e05bacaae0c72bd432
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Zastępuje tę metodę, aby wyszukać zabezpieczeń, integralności i tak dalej przed aktualizacje.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parametry  
 *status*  
 [in] Stan Oczekujące operacje na wiersze.  
  
 *hRowUpdate*  
 [in] Dojście do wierszy, do których użytkownik chce aktualizacji.  
  
 *pRowStatus*  
 [out] Zwrócony kod stanu dla użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli okaże się, że powinno być dozwolone aktualizacji, zwraca `S_OK`; w przeciwnym razie zwraca **E_FAIL**. Jeśli zezwolisz na aktualizację, należy również ustawić **DBROWSTATUS** w [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) do odpowiedniej [wiersz stanu](https://msdn.microsoft.com/en-us/library/ms722752.aspx).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetUpdateImpl, klasa](../../data/oledb/irowsetupdateimpl-class.md)