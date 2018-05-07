---
title: Prywatne funkcje wirtualne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 97b4d7d9f47901fa69aa50bfc6f405355cf378b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 