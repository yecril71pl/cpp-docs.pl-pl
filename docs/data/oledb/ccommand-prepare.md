---
title: CCommand::Prepare | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Prepare
- CCommand::Prepare
- Prepare
dev_langs:
- C++
helpviewer_keywords:
- Prepare method
ms.assetid: f0e473fc-2f7a-4d29-96c2-1328dc21e702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d029664508b6be71348aa3aa8d5801191f2aca3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089340"
---
# <a name="ccommandprepare"></a>CCommand::Prepare
Weryfikuje i optymalizuje bieżącego polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *cExpectedRuns*  
 [in] Ile razy można spodziewać się można wykonać polecenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda opakowuje metody OLE DB [ICommandPrepare::Prepare](https://msdn.microsoft.com/en-us/library/ms718370.aspx).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand, klasa](../../data/oledb/ccommand-class.md)