---
title: Prywatne funkcje wirtualne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6685edbe2e6e4805cadb38ada55624eaec2a7ce8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="private-virtual-functions"></a>Prywatne funkcje wirtualne
Prywatne funkcje wirtualne są obsługiwane w klasach pochodnych sposób zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W zarządzanych rozszerzeń poziom dostępu do funkcji wirtualnej nie ograniczyć jej możliwości do zastąpienia w klasie pochodnej. W nowej składni funkcji wirtualnej nie może przesłonić funkcji wirtualnej klasy podstawowej, która nie może uzyskać dostępu. Na przykład:  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible  
   void g();  
};  
```  
  
 Nie ma żadnych rzeczywistych mapowania tego rodzaju projektu na nowej składni. Po prostu jedną ma udostępnić elementów członkowskich klasy podstawowej — to znaczy prywatne. Dziedziczonej metody nie trzeba posiadać takie same prawa dostępu. W tym przykładzie najmniej inwazyjne zmiana ma na celu wprowadzić członka MyBaseClass `protected`. Dzięki temu program ogólne dostęp do metody za pomocą MyBaseClass nadal jest zabronione.  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 Należy pamiętać, że brak jawnych `virtual` — słowo kluczowe w klasie podstawowej, w obszarze nowej składni generuje ostrzeżenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 