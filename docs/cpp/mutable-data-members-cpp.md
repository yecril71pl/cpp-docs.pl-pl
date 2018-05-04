---
title: Modyfikowalne elementy członkowskie danych (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e7dd639cbf1ef076dee6e447f317533bf12dae10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mutable-data-members-c"></a>Modyfikowalne elementy członkowskie danych (C++)
To słowo kluczowe można stosować do elementów członkowskich danych niestatyczna i z systemem innym niż stała klasy. Jeśli element członkowski danych jest zadeklarowany jako `mutable`, wówczas jest można przypisać wartości do tego elementu członkowskiego danych z **const** funkcji członkowskiej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Uwagi  
 Na przykład następujący kod zostanie skompilowany bez błędów, ponieważ `m_accessCount` został zadeklarowany jako `mutable`i może być modyfikowany przez `GetFlag` mimo że `GetFlag` jest funkcją członkowską const.  
  
```  
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