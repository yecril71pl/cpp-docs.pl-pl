---
title: CRowset::GetApproximatePosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::GetApproximatePosition
- ATL::CRowset<TAccessor>::GetApproximatePosition
- CRowset.GetApproximatePosition
- CRowset::GetApproximatePosition
- GetApproximatePosition
- ATL.CRowset.GetApproximatePosition
- CRowset<TAccessor>::GetApproximatePosition
dev_langs: C++
helpviewer_keywords: GetApproximatePosition method
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165537f3b61120237e7bfb8330ecf353bc01a107
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetapproximateposition"></a>CRowset::GetApproximatePosition
Zwraca pozycję przybliżonej wiersz odpowiadający zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBookmark`  
 [in] Wskaźnik do zakładki, która identyfikuje wiersz, którego pozycja ma zostać znaleziona. **Wartość NULL** jeśli tylko liczba wierszy jest wymagana.  
  
 *pPosition*  
 [out] Wskaźnik do lokalizacji, gdzie `GetApproximatePosition` zwraca pozycję wiersza. **Wartość NULL** Jeśli pozycji nie jest wymagana.  
  
 `pcRows`  
 [out] Wskaźnik do lokalizacji, gdzie `GetApproximatePosition` zwraca całkowitą liczbę wierszy. **Wartość NULL** Jeśli liczba wierszy nie jest wymagana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs `IRowsetScroll`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetScroll** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
 Aby dowiedzieć się, jak korzystanie z zakładek użytkowników, zobacz [przy użyciu zakładki](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)