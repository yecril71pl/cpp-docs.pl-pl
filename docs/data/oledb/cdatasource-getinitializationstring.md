---
title: CDataSource::GetInitializationString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
dev_langs:
- C++
helpviewer_keywords:
- GetInitializationString method
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c2cc4652dcb7450217fd99969089bdbeb41c3a3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourcegetinitializationstring"></a>CDataSource::GetInitializationString
Pobiera ciąg inicjowania źródła danych, która jest obecnie otwarta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,   
   bool bIncludePassword = false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pInitializationString*  
 [out] Wskaźnik do ciągu inicjowania.  
  
 *bIncludePassword*  
 [in] **true** Jeśli ciąg zawiera hasło; w przeciwnym razie **false**.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Wynikowy ciąg inicjowania można potem ponownie otworzyć to połączenie ze źródłem danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)