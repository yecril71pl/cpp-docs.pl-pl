---
title: CXMLAccessor::GetXMLColumnData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLColumnData method
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 52b968dac5efbc4ceb41499a55c6be12d51dd0da
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cxmlaccessorgetxmlcolumndata"></a>CXMLAccessor::GetXMLColumnData
Pobiera informacje o typie kolumny tabeli jako dane ciągu w formacie XML, według kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `strOutput`  
 [out] Odwołanie do bufor ciąg zawierający informacje o typie kolumny mają zostać pobrane. Ten ciąg jest sformatowany w systemie nazwy tagu XML zgodne nazwy kolumn w magazynie danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Poniżej przedstawiono, jak informacje o typie kolumny jest sformatowany w kodzie XML. `type` Określa typ danych kolumny. Należy pamiętać, że typy danych są oparte na typach danych OLE DB nie te, które uzyskują dostęp do bazy danych.  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CXMLAccessor, klasa](../../data/oledb/cxmlaccessor-class.md)