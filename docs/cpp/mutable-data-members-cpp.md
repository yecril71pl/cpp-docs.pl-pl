---
title: Modyfikowalne składowe danych (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65d2fc42021a01a1260b57f9516e53c439c8e604
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947958"
---
# <a name="mutable-data-members-c"></a>Modyfikowalne elementy członkowskie danych (C++)
This — słowo kluczowe dotyczą wyłącznie elementy członkowskie danych niestatyczna i wartości innej niż stała klasy. Zadeklarowana składowa danych **mutable**, a następnie jest legalne, aby przypisać wartość do tego elementu członkowskiego danych, z **const** funkcja elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Uwagi  
 Na przykład, poniższy kod zostanie skompilowana bez błędów, ponieważ `m_accessCount` został zadeklarowany jako **mutable**i może być modyfikowana przez `GetFlag` mimo że `GetFlag` jest funkcją składową const.  
  
```cpp 
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)