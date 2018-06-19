---
title: Jawne przesłanianie elementu członkowskiego interfejsu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 811112d2721edccede6c7b4a278189fdec874523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110447"
---
# <a name="explicit-override-of-an-interface-member"></a>Jawne przesłanianie elementu członkowskiego interfejsu
Składnia deklaracji jawne przesłanianie elementu członkowskiego interfejsu w obrębie klasy zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Często chcesz podać dwa wystąpienia elementu członkowskiego interfejsu w klasie, który implementuje interfejs -, który jest używany podczas obiektów klasy dochodzi do zmiany zawartości za pomocą dojścia interfejsu i jest używany podczas obiektów klasy są używane za pośrednictwem interfejsu klasy. Na przykład:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 W zarządzanych rozszerzeń możemy to zrobić przez zapewnienie jawnej deklaracji metody interfejsu z metody nazwa kwalifikowana nazwą interfejsu. Wystąpienie klasy specyficzne jest niekwalifikowane. Eliminuje to potrzebę przypisanie elementu podrzędnego wartość zwracaną `Clone`, w tym przykładzie wywołanego jawne za pośrednictwem wystąpienia `R`.  
  
 W nowej składni ogólne mechanizm zastępowanie został wprowadzony zastępujący składni zarządzanych rozszerzeń. Naszym przykładzie będzie ponownie zapisać w następujący sposób:  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 Wersja ta wymaga, aby element członkowski interfejsu jawnie przesłaniana nadać unikatową nazwę w klasie. W tym miejscu zostały podane nieodpowiednich nazwę `InterfaceClone`. Zachowanie jest taka sama - wywołanie za pośrednictwem `ICloneable` zmienionej nazwie wywołuje interfejs `InterfaceClone`, podczas wywołania obiektu typu `R` wywołuje drugi `Clone` wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Jawne przesłonięcia](../windows/explicit-overrides-cpp-component-extensions.md)