---
title: CEnumerator::Find | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2466127dab53fa6646a4f149400e4318aed59970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094485"
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