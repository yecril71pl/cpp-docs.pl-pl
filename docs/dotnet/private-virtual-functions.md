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
ms.openlocfilehash: 0058d023268fa4d9ca5abe802ff45856e9855dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418076"
---
# <a name="private-virtual-functions"></a>Prywatne funkcje wirtualne

Sposób obsługi prywatne funkcje wirtualne w klasach pochodnych zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

W zarządzanych rozszerzeń poziom dostępu funkcji wirtualnej nie ogranicza możliwości został nadpisany w klasie pochodnej. W nowej składni funkcja wirtualna nie może przesłonić funkcję wirtualną klasę bazową, która nie może uzyskać dostępu. Na przykład:

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

Nie istnieje żadne rzeczywiste mapowanie tego rodzaju projektu na nowej składni. Jeden po prostu musi udostępnić składowych klasy bazowej — oznacza to, które nie są prywatne. Dziedziczonych metod nie trzeba mieć takie same prawa dostępu. W tym przykładzie najmniej inwazyjne zmiana ma na celu dołączyć MyBaseClass `protected`. Dzięki temu program ogólnego dostępu do metody za pomocą MyBaseClass nadal jest zabronione.

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

Należy pamiętać, że braku jawne `virtual` — słowo kluczowe w klasie bazowej, w ramach nowej składni generuje komunikat ostrzegawczy.

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
