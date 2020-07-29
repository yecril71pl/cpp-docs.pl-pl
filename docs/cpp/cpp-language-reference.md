---
title: Materiał referencyjny na temat języka C++
ms.custom: index-page
ms.date: 12/10/2019
helpviewer_keywords:
- C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 7b0d1227419aef3174d4f18b11cdc334879383b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221747"
---
# <a name="c-language-reference"></a>Materiał referencyjny na temat języka C++

W tym temacie wyjaśniono język programowania C++ zaimplementowanego w kompilatorze języka Microsoft C++. Organizacja jest oparta na *dokumentacji języka C++ z adnotacjami* , Margaret Ellis i Bjarne'a Stroustrupa oraz w standardzie międzynarodowym ANSI/ISO C++ (ISO/IEC FDIS 14882). Implementacje funkcji języka C++ specyficzne dla Microsoft są uwzględnione.

Aby zapoznać się z omówieniem nowoczesnych praktyk programowania w języku C++, zobacz [Witaj z powrotem w języku c++](welcome-back-to-cpp-modern-cpp.md).

Zobacz następujące tabele, aby szybko znaleźć słowo kluczowe lub operator:

- [Słowa kluczowe języka C++](../cpp/keywords-cpp.md)

- [Operatory języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>W tej sekcji

[Konwencje leksykalne](../cpp/lexical-conventions.md)<br/>
Podstawowe elementy leksykalne w programie C++: tokeny, komentarze, operatory, słowa kluczowe, separatory, literały. A także translacja pliku, pierwszeństwo/łączność operatorów.

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
Zakres, powiązanie, uruchamianie i kończenie programu, klasy magazynów i typy.

[Typy wbudowane](fundamental-types-cpp.md) Podstawowe typy, które są wbudowane w kompilator języka C++ i ich zakresy wartości.

[Konwersje standardowe](../cpp/standard-conversions.md)<br/>
Konwersje typu między typami wbudowanymi. Ponadto konwersje arytmetyczne i konwersje między wskaźnikiem, odwołaniem i typem wskaźnika do elementu członkowskiego.

[Deklaracje i definicje](declarations-and-definitions-cpp.md) Deklarowanie i Definiowanie zmiennych, typów i funkcji.

[Operatory, pierwszeństwo i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
Operatory w języku C++.

[Wyrażenia](../cpp/expressions-cpp.md)<br/>
Informacje na temat typów wyrażeń, semantyki wyrażeń, tematów odwołań do operatorów, rzutowania i operatorów rzutowania, typu środowiska uruchomieniowego.

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
Technika programowania, która niejawnie definiuje klasę obiektu funkcji i konstruuje obiekt funkcji tego typu klasy.

[Instrukcje](../cpp/statements-cpp.md)<br/>
Instrukcje wyrażeń, wartości null, złożeń, wyboru, iteracji, skoku i deklaracji.

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
Wprowadzenie do klas, struktur i unii. Ponadto funkcje członkowskie, specjalne funkcje składowe, elementy członkowskie danych, pola bitowe, **`this`** wskaźnik, klasy zagnieżdżone.

[Unie](unions.md)<br/>
Typy zdefiniowane przez użytkownika, w których wszyscy członkowie mają tę samą lokalizację w pamięci.

[Klasy pochodne](../cpp/inheritance-cpp.md)<br/>
Pojedyncze i wielokrotne dziedziczenie, **`virtual`** funkcje, wiele klas bazowych, klasy **abstrakcyjne** , reguły zakresu. Ponadto **`__super`** **`__interface`** słowa kluczowe i.

[Kontrola dostępu do elementów członkowskich](../cpp/member-access-control-cpp.md)<br/>
Kontrolowanie dostępu do składowych klasy: **`public`** , **`private`** i **`protected`** słów kluczowych. Funkcje i klasy zaprzyjaźnione.

[Przeciążenie](operator-overloading.md)<br/>
Przeciążone operatory, reguły dotyczące przeciążania operatora.

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
Obsługa wyjątków C++, obsługa wyjątków strukturalnych (SEH), słowa kluczowe używane w pisaniu instrukcji obsługi wyjątków.

[Potwierdzenia i komunikaty dostarczone przez użytkownika](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error`dyrektywa, **`static_assert`** słowo kluczowe, `assert` makro.

[Szablony](../cpp/templates-cpp.md)<br/>
Specyfikacje szablonów, szablony funkcji, szablony klas, **`typename`** słowa kluczowe, szablony a makra, szablony i inteligentne wskaźniki.

[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
Deklarowanie zdarzeń i programów obsługi zdarzeń.

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)<br/>
Modyfikatory specyficzne dla Microsoft C++. Adresowanie pamięci, konwencje wywoływania, **`naked`** funkcje, rozszerzone atrybuty klasy magazynu ( **`__declspec`** ), **`__w64`** .

[Asembler wbudowany](../assembler/inline/inline-assembler.md)<br/>
Używanie języka asemblera i C++ w **`__asm`** blokach.

[Obsługa kompilatora COM](../cpp/compiler-com-support.md)<br/>
Odwołanie do klas specyficznych dla Microsoft i globalne funkcje używane do obsługi typów modelu COM.

[Rozszerzenia Microsoft](../cpp/microsoft-extensions.md)<br/>
Rozszerzenia firmy Microsoft do języka C++.

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)<br/>
Informacje o niestandardowym zachowaniu kompilatora języka Microsoft C++.

[Witamy ponownie w języku C++](welcome-back-to-cpp-modern-cpp.md)<br/>
Omówienie nowoczesnych rozwiązań programistycznych języka C++ do pisania bezpiecznych, prawidłowych i wydajnych programów.

## <a name="related-sections"></a>Sekcje pokrewne

[Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)<br/>
Materiały referencyjne na temat używania kompilatora języka Microsoft C++ do celu platformy .NET.

[Odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md)<br/>
Opcje kompilatora, opcje konsolidatora i inne narzędzia kompilacji.

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Materiał referencyjny na temat pragm, dyrektyw preprocesora, wstępnie zdefiniowanych makr i preprocesora.

[Biblioteki Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Lista linków do stron początkowych odwołań dla różnych bibliotek języka Microsoft C++.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C](../c-language/c-language-reference.md)
