---
title: "alignment_of — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3bd3f2e306c09e69a37bef08f75fd33efb6fcb7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="alignmentof-class"></a>alignment_of — Klasa
Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w postaci liczby [alignof](../cpp/alignof-and-alignas-cpp.md). Użyj `alignof` bezpośrednio po prostu konieczność wartość wyrównania zapytania. Alignment_of — należy używać wtedy, gdy konieczne stałej, na przykład podczas wysyłania tagu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct alignment_of;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Kwerenda typu przechowuje wartość wyrównania typu `Ty`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [aligned_storage, klasa](../standard-library/aligned-storage-class.md)
