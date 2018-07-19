---
title: Klasy i struktury (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88836d93d6ce3ba4dff817c7b470e87f48f61b14
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954180"
---
# <a name="classes-and-structs-c"></a>Klasy i struktury (C++)
Ta sekcja wprowadza C++ klas i struktur. Konstrukcje dwa są identyczne w języku C++, z tą różnicą, że w strukturach publiczne, jest wartość domyślna dostępu, natomiast w klasach, wartością domyślną jest prywatny.  
  
 Klasy i struktury są konstrukcje, według których należy zdefiniować własne typy. Klasy i struktury można zawierają elementy członkowskie danych i funkcje Członkowskie, które umożliwiają opisują typ stanem i zachowaniem.  
  
 Uwzględnione są następujące tematy:  
  
-   [class](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Omówienie składowej klasy](../cpp/class-member-overview.md)  
  
-   [Kontrola dostępu do składowych](../cpp/member-access-control-cpp.md)  
  
-   [Dziedziczenie](../cpp/inheritance-cpp.md)  
  
-   [Statyczne składowe](../cpp/static-members-cpp.md)  
  
-   [Konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [Modyfikowalne elementy członkowskie danych (specyfikator modyfikowalny)](../cpp/mutable-data-members-cpp.md)  
  
-   [Zagnieżdżone deklaracje klas](../cpp/nested-class-declarations.md)  
  
-   [Anonimowe typy klas](../cpp/anonymous-class-types.md)  
  
-   [Wskaźniki do składowych](../cpp/pointers-to-members.md)  
  
-   [this, wskaźnik](../cpp/this-pointer.md)  
  
-   [Pola bitowe języka C++](../cpp/cpp-bit-fields.md)  
  
 Typy trzy klasy są struktury, klasy lub union. Są deklarowane za pomocą [struktury](../cpp/struct-cpp.md), [klasy](../cpp/class-cpp.md), i [Unii](../cpp/unions.md) słów kluczowych. W poniższej tabeli przedstawiono różnice między typami trzy klasy.  
  
 Aby uzyskać więcej informacji na temat Unii, zobacz [unie](../cpp/unions.md). Aby uzyskać informacje dotyczące zarządzanych klas i struktur, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Kontrola dostępu i ograniczenia struktury, klasy i unie  
  
|Struktury|Klasy|Unie|  
|----------------|-------------|------------|  
|klucz klasy jest **— struktura**|klucz klasy jest **klasy**|klucz klasy jest **Unii**|  
|Dostęp domyślny jest publiczny|Dostęp domyślny jest prywatny|Dostęp domyślny jest publiczny|  
|Bez ograniczeń użycia|Bez ograniczeń użycia|Użyj tylko jednego członka w czasie|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)