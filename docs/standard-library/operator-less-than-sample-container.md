---
title: "operator&lt; (&lt;przykładowy kontener&gt;) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
dev_langs: C++
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f7aab9f32e51123f15169f5ccbb591ff2d30b67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;przykładowy kontener&gt;)
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
 Overloads **operatora <** do porównywania dwóch obiektów klasy szablonu [kontenera](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
bool operator<(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.  
  
## <a name="see-also"></a>Zobacz też  
[\<Przykładowy kontener >](../standard-library/sample-container.md)  
[Rozpocznij](../standard-library/container-class-begin.md)  
[koniec](../standard-library/container-class-end.md)  