---
title: Klasy i struktury (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d5f690846954dde21252b2aabdd229abdf33ec6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="classes-and-structs-c"></a>Klasy i struktury (C++)
W tej sekcji przedstawiono C++ klas i struktur. Dwa konstrukcje są takie same jak w języku C++, ale w strukturach dostępność domyślny jest publiczny, w klasach wartość domyślna jest prywatny.  
  
 Klasy i struktury są konstrukcje, zgodnie z którymi Definiowanie własnych typów. Klasy i struktury mogą jednocześnie zawierać elementów członkowskich danych i funkcji Członkowskich, które umożliwiają opisano stanu i zachowania typu.  
  
 Omówiono następujące zagadnienia:  
  
-   [klasy](../cpp/class-cpp.md)  
  
-   [— Struktura](../cpp/struct-cpp.md)  
  
-   [Omówienie elementu członkowskiego klasy](../cpp/class-member-overview.md)  
  
-   [Kontrola dostępu do elementów członkowskich](../cpp/member-access-control-cpp.md)  
  
-   [Dziedziczenie](../cpp/inheritance-cpp.md)  
  
-   [Statyczne elementy członkowskie](../cpp/static-members-cpp.md)  
  
-   [Konwersje zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [Modyfikowalne elementy członkowskie danych (specyfikator modyfikowalny)](../cpp/mutable-data-members-cpp.md)  
  
-   [Zagnieżdżone deklaracje klas](../cpp/nested-class-declarations.md)  
  
-   [Anonimowe typy klas](../cpp/anonymous-class-types.md)  
  
-   [Wskaźniki do elementów członkowskich](../cpp/pointers-to-members.md)  
  
-   [this, wskaźnik](../cpp/this-pointer.md)  
  
-   [Pola bitowe języka C++](../cpp/cpp-bit-fields.md)  
  
 Klasa trzy typy struktury, klasy lub union. Są one uznane za pomocą [struktury](../cpp/struct-cpp.md), [klasy](../cpp/class-cpp.md), i [Unii](../cpp/unions.md) słowa kluczowe (zobacz [Definiowanie typu klasy](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da)). W poniższej tabeli przedstawiono różnice między typami trzy klasy.  
  
 Aby uzyskać więcej informacji, Unii, zobacz [unie](../cpp/unions.md). Informacje dotyczące zarządzanych klas i struktur, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Kontrola dostępu i ograniczenia, struktur i Unii  
  
|Struktury|Klasy|Unie|  
|----------------|-------------|------------|  
|klucz klasy`struct`|klucz klasy jest **— klasa**|klucz klasy jest **Unii**|  
|Dostęp do domyślnej jest publiczny|Dostęp do domyślnej jest prywatny|Dostęp do domyślnej jest publiczny|  
|Brak ograniczeń użycia|Brak ograniczeń użycia|Użyj tylko jeden element członkowski w czasie|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)