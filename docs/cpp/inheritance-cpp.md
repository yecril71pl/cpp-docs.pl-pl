---
title: Dziedziczenie (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: ab8425a916eb96f6419c67a76fa401716ad84631
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232264"
---
# <a name="inheritance--c"></a>Dziedziczenie (C++)

W tej sekcji wyjaśniono, jak używać klas pochodnych do tworzenia rozszerzalnych programów.

## <a name="overview"></a>Omówienie

Nowe klasy mogą pochodzić z istniejących klas przy użyciu mechanizmu o nazwie "dziedziczenie" (zobacz informacje zaczynające się [pojedynczym dziedziczeniem](../cpp/single-inheritance.md)). Klasy, które są używane do wyprowadzania są nazywane "klasami podstawowymi" określonej klasy pochodnej. Klasa pochodna jest zadeklarowana przy użyciu następującej składni:

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

Po tagu (nazwie) klasy zostanie wyświetlony dwukropek, po którym następuje lista specyfikacji podstawowych.  Klasy bazowe, dlatego nazwane, muszą zostać zadeklarowane wcześniej.  Specyfikacje podstawowe mogą zawierać specyfikator dostępu, który jest jednym ze słów kluczowych **`public`** **`protected`** lub **`private`** .  Te specyfikatory dostępu są wyświetlane przed nazwą klasy bazowej i mają zastosowanie tylko do tej klasy bazowej.  Te specyfikatory kontrolują uprawnienia klasy pochodnej do użycia do elementów członkowskich klasy podstawowej.  Aby uzyskać informacje na temat dostępu do elementów członkowskich klasy bazowej, zobacz [Access Control elementu członkowskiego](../cpp/member-access-control-cpp.md) .  Jeśli specyfikator dostępu zostanie pominięty, jest brany pod uwagę dostęp do tej bazy **`private`** .  Specyfikacje podstawowe mogą zawierać słowo kluczowe, **`virtual`** Aby wskazać wirtualne dziedziczenie.  Słowo kluczowe może występować przed lub Po specyfikatorze dostępu, jeśli istnieje.  Jeśli jest używane wirtualne dziedziczenie, Klasa bazowa jest nazywana wirtualną klasą bazową.

Można określić wiele klas podstawowych, rozdzielając je przecinkami.  W przypadku określenia pojedynczej klasy bazowej model dziedziczenia jest [pojedynczym dziedziczeniem](../cpp/single-inheritance.md). Jeśli określono więcej niż jedną klasę bazową, model dziedziczenia jest nazywany [wielokrotnym dziedziczeniem](../cpp/multiple-base-classes.md).

Dostępne są następujące tematy:

- [Pojedyncze dziedziczenie](../cpp/single-inheritance.md)

- [Wiele klas podstawowych](../cpp/multiple-base-classes.md)

- [Funkcji wirtualnych](../cpp/virtual-functions.md)

- [Jawne przesłonięcia](../cpp/explicit-overrides-cpp.md)

- [Klasy abstrakcyjne](../cpp/abstract-classes-cpp.md)

- [Podsumowanie reguł zakresu](../cpp/summary-of-scope-rules.md)

Słowa kluczowe [__super](../cpp/super.md) i [__interface](../cpp/interface.md) są udokumentowane w tej sekcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
