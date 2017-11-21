---
title: operator&gt;= | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- operator>=
- std::>=
- std.operator>=
- '>='
- std.>=
- std::operator>=
dev_langs: C++
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator >=
- operator>=
ms.assetid: 14fbebf5-8b75-4afa-a51b-3112d31c07cf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3a4ec3783e29a3383ad6e1e70d052e5e24cee38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="operatorgt"></a>operator&gt;=
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
 Overloads **operator > =** do porównywania dwóch obiektów klasy szablonu [kontenera](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
bool operator>=(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `!(left < right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Przykładowy kontener >](../standard-library/sample-container.md)

