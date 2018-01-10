---
title: "operator&gt; (&lt;przykładowy kontener&gt;) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
dev_langs: C++
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 047132a1281a33f3f93b5dc3afe5b0807a63b6bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;przykładowy kontener&gt;)
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
 Overloads **operatora >** do porównywania dwóch obiektów klasy szablonu [kontenera](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
bool operator*gt;(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `right < left`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Przykładowy kontener >](../standard-library/sample-container.md)

