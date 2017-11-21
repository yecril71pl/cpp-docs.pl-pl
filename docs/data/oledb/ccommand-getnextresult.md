---
title: CCommand::GetNextResult | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs: C++
helpviewer_keywords: GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a0b4c03d7aa31949752e4362380d1705d7db6e9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Pobiera następnego wyniku, jeśli jest dostępny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetNextResult(  
   DBROWCOUNT* pulRowsAffected,  
   bool bBind = true   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *pulRowsAffected*  
 [We/Wy] Wskaźnik do pamięci, w której jest zwracana liczba wierszy, których to dotyczy, za pomocą polecenia.  
  
 `bBind`  
 [in] Określa, czy można powiązać polecenie automatycznie po wykonywana. Wartość domyślna to **true**, co powoduje, że polecenie może być powiązane automatycznie. Ustawienie `bBind` do **false** uniemożliwia automatyczne powiązania polecenie tak, aby można powiązać ręcznie. (Ręczne powiązanie jest znaczący użytkownikom OLAP).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zestaw wyników zostaną pobrane wcześniej, ta funkcja zwalnia poprzedniego zestawu wyników i usuwa powiązanie kolumn. Jeśli `bBind` jest **true**, tworzy ona powiązanie nowe kolumny.  
  
 Tej funkcji należy wywołać tylko wtedy, gdy określono wiele wyników przez ustawienie `CCommand` parametr szablonu *TMultiple*=`CMultipleResults`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand — klasa](../../data/oledb/ccommand-class.md)