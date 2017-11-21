---
title: "Modyfikowalne elementy członkowskie danych (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: mutable_cpp
dev_langs: C++
helpviewer_keywords: mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a3c960c5fcf5a73d339b7565cd0bec38dba98f12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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