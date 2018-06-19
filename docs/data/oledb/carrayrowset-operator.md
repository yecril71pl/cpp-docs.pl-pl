---
title: CArrayRowset::operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755e484f430f47eb072e3c590bfbee8471984bb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089130"
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