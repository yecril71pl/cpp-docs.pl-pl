---
title: CEnumerator::Find | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 66298c4be2bb1e43aa37899fe652ccbf6694faae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
Sprawdza, czy określona nazwa spośród dostępnych dostawców.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *szSearchName*  
 [in] Nazwy do wyszukania.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli znaleziono nazwy. W przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 Ta nazwa jest mapowany na **SOURCES_NAME** członkiem [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CEnumerator, klasa](../../data/oledb/cenumerator-class.md)