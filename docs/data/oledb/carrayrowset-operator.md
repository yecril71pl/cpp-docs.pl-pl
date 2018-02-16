---
title: CArrayRowset::operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs:
- C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0921ad4c574c496656ec616d1d569158c596c5ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
Udostępnia składni tablicy do uzyskiwania dostępu do wiersza w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Parametr opartego na szablonie, który określa typ metody dostępu przechowywany w zestawie wierszy.  
  
 `nRow`  
 [in] Numer wiersza (elementu tablicy) chcesz uzyskać dostęp.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawartość żądanego wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `nRow` przekracza liczbę wierszy w zestawie wierszy, jest zgłaszany wyjątek.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CArrayRowset, klasa](../../data/oledb/carrayrowset-class.md)