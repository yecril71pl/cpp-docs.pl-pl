---
title: CRowset::Undo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset.Undo
- ATL::CRowset<TAccessor>::Undo
- CRowset<TAccessor>::Undo
- ATL.CRowset.Undo
- ATL.CRowset<TAccessor>.Undo
- CRowset<TAccessor>.Undo
- ATL::CRowset::Undo
- CRowset::Undo
- Undo
dev_langs: C++
helpviewer_keywords: Undo method
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33213cb9780846639de6638bc3028a3e656d1a9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetundo"></a>CRowset::Undo
Cofa zmiany wprowadzone od czasu ostatniego pobrania wiersza lub [aktualizacji](../../data/oledb/crowset-update.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT Undo(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Wskaźnik do lokalizacji, gdzie **Cofnij** zwraca liczbę wierszy w podjęciu próby cofnięcia, jeśli jest to wymagane.  
  
 `phRow`  
 [out] Wskaźnik do lokalizacji, gdzie **Cofnij** zwraca tablicę dojść do wszystkich wierszy podjęciu próby cofnięcia, jeśli jest to wymagane.  
  
 `pStatus`  
 [out] Wskaźnik do lokalizacji, gdzie **Cofnij** zwraca wartość stanu wiersza. Brak stanu jest zwracany, gdy `pStatus` ma wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs `IRowsetUpdate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetUpdate** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)