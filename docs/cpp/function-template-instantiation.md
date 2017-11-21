---
title: "Tworzenie wystąpienia szablonu funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fafeb199acfb4422f2e08fe8971fa39752461a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-template-instantiation"></a>Tworzenie wystąpienia szablonu funkcji
Gdy szablonu funkcji najpierw zostanie wywołana dla każdego typu, kompilator tworzy wystąpienia. Każdego wystąpienia jest wersja szablonem funkcji przeznaczone dla typu. Tego wystąpienia zostanie wywołana za każdym razem, gdy funkcja jest używana dla typu. Jeśli masz kilka wystąpień identyczne, nawet w różnych modułach tylko jedna kopia wystąpienia zakończą się w pliku wykonywalnego.  
  
 Konwersja argumentów funkcji jest dozwolony w szablonów funkcji dla każdej pary argumentów i parametrów, gdy parametr nie jest zależny od argumentu szablonu.  
  
 Szablony funkcji może zostać jawnie utworzone przez zadeklarowanie szablonu z określonego typu jako argumentu. Na przykład następujący kod jest dozwolone:  
  
```cpp
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony funkcji](../cpp/function-templates.md)
