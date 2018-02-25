---
title: "is_placeholder — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5491f0a8c5ef0c6999680beb8b82cd6280f87af1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="isplaceholder-class"></a>is_placeholder — Klasa
Testy, jeśli typ symbolu zastępczego.  
  
## <a name="syntax"></a>Składnia  
  
{is_placeholder — struktura  
   statyczne stałej wartości int;  
   };  
  
## <a name="remarks"></a>Uwagi  
 Stała wartość `value` wynosi 0, jeśli typ `Ty` nie jest symbolem zastępczym; w przeciwnym razie jego wartość to pozycja argumentu wywołania funkcji, który tworzy ona powiązanie z. Służy do określenia wartości `N` n-tego symbolu zastępczego `_N`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}  
```  
  
```Output  
0  
3  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt _1](../standard-library/1-object.md)

