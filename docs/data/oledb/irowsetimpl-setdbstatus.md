---
title: IRowsetImpl::SetDBStatus | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
dev_langs: C++
helpviewer_keywords: SetDBStatus method
ms.assetid: b73f526a-4fc6-4adb-9611-c3cca2cddb23
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dcc6783ce210c434e58814bcee8654ddd9111b52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplsetdbstatus"></a>IRowsetImpl::SetDBStatus
Ustawia `DBSTATUS` flagi stanu dla określonego pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      virtual HRESULT SetDBStatus(  
   DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `statusFlags`  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) flagi można ustawić dla tej kolumny.  
  
 `currentRow`  
 Bieżącego wiersza.  
  
 *wartości elementu columnInfo*  
 Kolumna, dla którego stan jest ustawiony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="remarks"></a>Uwagi  
 Dostawca zastępuje specjalnego przetwarzania dla tej funkcji **DBSTATUS_S_ISNULL** i **DBSTATUS_S_DEFAULT**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)