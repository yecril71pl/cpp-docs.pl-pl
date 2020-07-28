---
title: Klasy i struktury (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: d593f6575fec64aa0eb14c7aa0fcbb5c4eb66691
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220603"
---
# <a name="classes-and-structs-c"></a>Klasy i struktury (C++)

Ta sekcja zawiera wprowadzenie do klas i struktur języka C++. Te dwa konstrukcje są identyczne w języku C++, z tą różnicą, że w strukturach domyślna dostępność jest publiczna, natomiast w klasach jest to ustawienie domyślne Private.

Klasy i struktury są konstrukcjami, w których można definiować własne typy. Klasy i struktury mogą zawierać zarówno składowe danych, jak i funkcje członkowskie, które umożliwiają opisywanie stanu i zachowania typu.

Dostępne są następujące tematy:

- [określonej](../cpp/class-cpp.md)

- [konstrukcja](../cpp/struct-cpp.md)

- [Przegląd składowej klasy](../cpp/class-member-overview.md)

- [Access Control elementu członkowskiego](../cpp/member-access-control-cpp.md)

- [Dziedziczenie](../cpp/inheritance-cpp.md)

- [Statyczne elementy członkowskie](../cpp/static-members-cpp.md)

- [Konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)

- [Modyfikowalne składowe danych (specyfikator modyfikowalny)](../cpp/mutable-data-members-cpp.md)

- [Zagnieżdżone deklaracje klas](../cpp/nested-class-declarations.md)

- [Anonimowe typy klas](../cpp/anonymous-class-types.md)

- [Wskaźniki do elementów członkowskich](../cpp/pointers-to-members.md)

- [Ten wskaźnik](../cpp/this-pointer.md)

- [Pola bitowe C++](../cpp/cpp-bit-fields.md)

Trzy typy klas to struktura, Klasa i Unia. Są one deklarowane przy użyciu [struktur](../cpp/struct-cpp.md), [klas](../cpp/class-cpp.md)i [słów kluczowych](../cpp/unions.md) . W poniższej tabeli przedstawiono różnice między trzema typami klas.

Aby uzyskać więcej informacji na temat Unii, zobacz [Unions](../cpp/unions.md). Aby uzyskać informacje dotyczące klas i struktur w językach C++/CLI i C++/CX, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Access Control i ograniczenia struktur, klas i Unii

|Struktury|Klasy|Unie|
|----------------|-------------|------------|
|klucz klasy to**`struct`**|klucz klasy to**`class`**|klucz klasy to**`union`**|
|Domyślny dostęp jest publiczny|Domyślny dostęp jest prywatny|Domyślny dostęp jest publiczny|
|Brak ograniczeń użycia|Brak ograniczeń użycia|Używaj tylko jednej składowej naraz|

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
