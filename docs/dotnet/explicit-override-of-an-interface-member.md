---
title: Jawne przesłanianie składowej interfejsu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409028"
---
# <a name="explicit-override-of-an-interface-member"></a>Jawne przesłanianie elementu członkowskiego interfejsu

Składnia do deklarowania jawnego przesłaniania elementu członkowskiego interfejsu w klasie został zmieniony z zarządzanych rozszerzeń języka C++ do Visual C++.

Często chcą zapewnić dwa wystąpienia elementu członkowskiego interfejsu w klasie, który implementuje interfejs — taki, który jest używany, gdy obiekty klasy są zmieniane przez dojście interfejsu i jest używany, gdy są używane obiekty klasy za pomocą interfejsu klasy. Na przykład:

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

W zarządzanych rozszerzeń możemy to zrobić, podając jawnej deklaracji metody interfejsu o nazwie metody kwalifikowana nazwą interfejsu. Wystąpienie swoiste dla klas jest niekwalifikowane. Eliminuje to konieczność downcast wartość zwracaną przez `Clone`, w tym przykładzie jawne wywoływanym za pośrednictwem wystąpienia `R`.

W nowej składni ogólny mechanizm nadrzędnych wprowadzono zastępujący składni zarządzanych rozszerzeń. Nasz przykład może zostać przepisane, w następujący sposób:

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

Tej poprawki wymaga, aby składowej interfejsu jawnie przesłaniana nadać unikatową nazwę w klasie. W tym miejscu został podany niewygodna nazwę `InterfaceClone`. Zachowanie jest taka sama - wywołania za pośrednictwem `ICloneable` zmienionej nazwie wywołuje interfejs `InterfaceClone`, podczas gdy wywołaniu do obiektu typu `R` wywołuje drugi `Clone` wystąpienia.

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[Jawne przesłonięcia](../windows/explicit-overrides-cpp-component-extensions.md)