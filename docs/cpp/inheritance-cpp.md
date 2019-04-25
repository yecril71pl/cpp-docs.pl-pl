---
title: Dziedziczenie (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 0180a2f7b41e3169bc9e25d8b598dbe2b84be088
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184583"
---
# <a name="inheritance--c"></a>Dziedziczenie (C++)

W tej sekcji wyjaśniono, jak za pomocą klasy pochodne tworzyć rozszerzalne programów.

## <a name="overview"></a>Omówienie

Nowe klasy mogą być uzyskane z istniejących klas przy użyciu mechanizmu o nazwie "dziedziczenie" (zobacz informacje o począwszy [pojedyncze dziedziczenie](../cpp/single-inheritance.md)). Klasy, które są używane do wyprowadzenia są nazywane "klasy bazowej" konkretnej klasy pochodnej. Klasy pochodnej jest zadeklarowana, używając następującej składni:

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

Po tagu (nazwa) dla klasy dwukropek pojawia się po nich lista podstawowej specyfikacji.  Klasy bazowe, więc o nazwie musi mieć uprzednio zadeklarowany.  Podstawowej specyfikacji mogą zawierać specyfikator dostępu, który jest jednym z kluczowych **publicznych**, **chronione** lub **prywatnej**.  Te specyfikatory dostępu pojawiają się przed nazwą klasy bazowej i mają zastosowanie tylko do tej klasy bazowej.  Te specyfikatory kontrolować uprawnienia klasy pochodnej do użycia do elementów członkowskich klasy podstawowej.  Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) uzyskać informacji na temat dostępu do składowych klasy podstawowej.  W przypadku pominięcia specyfikatora dostępu jest uznawany za dostęp do tej bazy **prywatnej**.  Specyfikacje podstawowych może zawierać słowa kluczowego **wirtualnego** do wskazania dziedziczenie wirtualne.  This — słowo kluczowe może pojawić się przed lub po specyfikatorze dostępu, jeśli istnieje.  Jeśli dziedziczenie wirtualne jest używany, klasa bazowa nazywa się wirtualnej klasy bazowej.

Można określić wielu klas bazowych, oddzielonych przecinkami.  Jeśli pojedyncza klasa bazowa jest określony, model dziedziczenia jest [pojedyncze dziedziczenie](../cpp/single-inheritance.md). Jeżeli określono więcej niż jednej klasy bazowej, nosi nazwę modelu dziedziczenia [wielokrotne dziedziczenie](../cpp/multiple-base-classes.md).

Uwzględnione są następujące tematy:

- [Pojedyncze dziedziczenie](../cpp/single-inheritance.md)

- [Wiele klas podstawowych](../cpp/multiple-base-classes.md)

- [Funkcje wirtualne](../cpp/virtual-functions.md)

- [Jawne przesłonięcia](../cpp/explicit-overrides-cpp.md)

- [Klasy abstrakcyjne](../cpp/abstract-classes-cpp.md)

- [Podsumowanie reguł zakresu](../cpp/summary-of-scope-rules.md)

[__Super](../cpp/super.md) i [__interface](../cpp/interface.md) słowa kluczowe są opisane w tej sekcji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)