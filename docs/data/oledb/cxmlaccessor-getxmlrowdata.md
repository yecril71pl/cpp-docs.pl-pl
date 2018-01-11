---
title: CXMLAccessor::GetXMLRowData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs: C++
helpviewer_keywords: GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1cfd67065b267f01704bb0658b89d9bab2186100
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
Pobiera całą zawartość tabeli jako dane ciągu w formacie XML, według wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetXMLRowData(   
   CSimpleStringW& strOutput,   
   bool bAppend = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `strOutput`  
 [out] Odwołanie do buforu zawierające dane w tabeli mają zostać pobrane. Dane są sformatowane jako ciąg danych za pomocą nazwy tagu XML zgodne nazwy kolumn w magazynie danych.  
  
 *bAppend*  
 [in] Wartość logiczna określająca, czy ma zostać dołączony ciąg na końcu danych wyjściowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Poniżej przedstawiono sposób formatowania danych wiersza w kodzie XML. `DATA`poniżej reprezentuje wiersz danych. Użyj Przenieś metody, aby przejść do żądanego wiersza.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CXMLAccessor, klasa](../../data/oledb/cxmlaccessor-class.md)