---
title: CRowset::GetOriginalData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.GetOriginalData
- CRowset<TAccessor>::GetOriginalData
- GetOriginalData
- ATL::CRowset<TAccessor>::GetOriginalData
- ATL.CRowset.GetOriginalData
- CRowset::GetOriginalData
- ATL::CRowset::GetOriginalData
- CRowset.GetOriginalData
dev_langs: C++
helpviewer_keywords: GetOriginalData method
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7a1c5fe26d17ac353138abc21b3ae46d9a72101
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetoriginaldata"></a>CRowset::GetOriginalData
Wywołania **IRowsetUpdate::GetOriginalData** do pobierania danych ostatnio pobrana z lub przesłana do źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
HRESULT GetOriginalData( ) throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera dane ostatnio pobrana z lub przesłana do źródła danych; nie pobiera wartości na podstawie oczekujące zmiany.  
  
 Ta metoda wymaga opcjonalny interfejs `IRowsetUpdate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetUpdate** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)