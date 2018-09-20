---
title: Pieczętowanie funkcji wirtualnej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385186"
---
# <a name="sealing-a-virtual-function"></a>Pieczętowanie funkcji wirtualnej

Składnia pieczętowanie funkcji wirtualnej zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

`__sealed` — Słowo kluczowe jest używane w zarządzanych rozszerzeń do modyfikowania któregokolwiek typu odwołania, nie można przydzielać kolejnych pochodnym (zobacz [deklaracja zarządzanego typu klasy](../dotnet/declaration-of-a-managed-class-type.md)), lub zmodyfikować funkcję wirtualną, nie można przydzielać kolejne przesłanianie metody w klasie pochodnej. Na przykład:

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

W tym przykładzie `derived::f()` zastępuje `base::f()` wystąpienia oparte na dokładne dopasowanie prototypu funkcji. `__sealed` Słowo kluczowe wskazuje, że kolejne klasy dziedziczone z klasy pochodnej nie może dostarczyć zastąpieniu obiektu `derived::f()`.

W nowej składni `sealed` jest umieszczany po podpis, a nie będą mogli się występować w dowolnym miejscu przed prototypu funkcji rzeczywiste, ponieważ została wcześniej. Ponadto użycie `sealed` wymaga jawnego użycia `virtual` — słowo kluczowe, jak również. Oznacza to, że poprawne tłumaczenie `derived`powyżej, jest następujący:

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

Brak `virtual` — słowo kluczowe, w tym wystąpieniu powoduje wystąpienie błędu. W nowej składni, kontekstowe słowo kluczowe `abstract` mogą być używane zamiast `=0` do wskazania czystej funkcji wirtualnej. To nie jest obsługiwana w ramach zarządzanych rozszerzeń. Na przykład:

```
__gc class base { public: virtual void f()=0; };
```

może być napisany

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)