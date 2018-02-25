---
title: CCommand::SetParameterInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- SetParameterInfo method
ms.assetid: a70e92f4-1e73-41d7-a5b7-c6ebb45a6477
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 453ee4337e18ee20844631eee12ebf724bde2b2b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandsetparameterinfo"></a>CCommand::SetParameterInfo
Określa typ macierzysty każdego parametru polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ICommandWithParameters::SetParameterInfo](https://msdn.microsoft.com/en-us/library/ms725393.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand, klasa](../../data/oledb/ccommand-class.md)