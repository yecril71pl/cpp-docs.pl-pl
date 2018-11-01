---
title: Materiał referencyjny na temat języka C++
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 69b244a1559a4570cc00a72d86426a7929ffc474
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469384"
---
# <a name="c-language-reference"></a>Materiał referencyjny na temat języka C++

To źródło odniesienia wyjaśnia sposób implementacji C++ w Microsoft Visual C++. Organizacja jest oparta na *The Annotated C++ Reference Manual* autorstwa Margaret Ellis i Bjarne'a Stroustrupa oraz na ANSI/ISO C++ Międzynarodowy Standard (ISO/IEC FDIS 14882). Implementacje funkcji języka C++ specyficzne dla Microsoft są uwzględnione.

Omówienie rozwiązania w zakresie programowania nowoczesnym języku C++, zobacz [powitalnej zwrotnie do C++](welcome-back-to-cpp-modern-cpp.md).

Zobacz następujące tabele, aby szybko znaleźć słowo kluczowe lub operator:

- [Słowa kluczowe języka C++](../cpp/keywords-cpp.md)

- [Operatory języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>W tej sekcji

[Konwencje leksykalne](../cpp/lexical-conventions.md)<br/>
Podstawowe elementy leksykalne w programie C++: tokeny, komentarze, operatory, słowa kluczowe, separatory, literały. A także translacja pliku, pierwszeństwo/łączność operatorów.

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
Zakres, powiązanie, uruchamianie i kończenie programu, klasy magazynów i typy.

[Konwersje standardowe](../cpp/standard-conversions.md)<br/>
Konwersje typu między typami wbudowanymi lub „podstawowymi”. Ponadto konwersje arytmetyczne i konwersje między wskaźnikiem, odwołaniem i typem wskaźnika do elementu członkowskiego.

[Operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
Operatory w języku C++.

[Wyrażenia](../cpp/expressions-cpp.md)<br/>
Informacje na temat typów wyrażeń, semantyki wyrażeń, tematów odwołań do operatorów, rzutowania i operatorów rzutowania, typu środowiska uruchomieniowego.

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
Technika programowania, która niejawnie definiuje klasę obiektu funkcji i konstruuje obiekt funkcji tego typu klasy.

[Instrukcje](../cpp/statements-cpp.md)<br/>
Instrukcje wyrażeń, wartości null, złożeń, wyboru, iteracji, skoku i deklaracji.

[Deklaracje i definicje](declarations-and-definitions-cpp.md)<br/>
Specyfikatory klasy magazynowej, definicje funkcji, inicjalizacje, wyliczenia, **klasy**, **struktury**, i **Unii** deklaracji, i **— typedef**  deklaracji. Ponadto **wbudowane** funkcji **const** — słowo kluczowe, przestrzenie nazw.

[Klas, struktur i Unii](../cpp/classes-and-structs-cpp.md)<br/>
Wprowadzenie do klas, struktur i unii. Ponadto funkcje Członkowskie, specjalnych funkcji składowych, składowe danych, pola bitowe, **to** wskaźnika, klasy zagnieżdżone.

[Klasy pochodne](../cpp/inheritance-cpp.md)<br/>
Dziedziczenie pojedyncze lub wielokrotne, **wirtualnego** funkcje, wiele klas bazowych, **abstrakcyjne** klasy, reguły zakresu. Ponadto **__super** i **__interface** słów kluczowych.

[Kontrola dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md)<br/>
Kontrolowanie dostępu do składowych klasy: **publicznych**, **prywatnej**, i **chronione** słów kluczowych. Funkcje i klasy zaprzyjaźnione.

[Przeciążenie](operator-overloading.md)<br/>
Przeciążone operatory, zasady dotyczące przeciążania operatorów.

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
Obsługa wyjątków C++, obsługa wyjątków strukturalnych (SEH), słowa kluczowe używane w pisaniu instrukcji obsługi wyjątków.

[Potwierdzenia i komunikaty dostarczane przez użytkownika](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` dyrektywy, **static_assert** — słowo kluczowe, `assert` makra.

[Szablony](../cpp/templates-cpp.md)<br/>
Specyfikacje szablonu, funkcja szablonów, szablony klas **typename** — słowo kluczowe, szablony a makra, szablony i inteligentne wskaźniki.

[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
Deklarowanie zdarzeń i programów obsługi zdarzeń.

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)<br/>
Modyfikatory specyficzne dla Microsoft C++. Pamięć adresowania, Konwencje wywoływania, **"naked"** funkcje, rozszerzone atrybuty klasy magazynu (**__declspec**), **__w64**.

[Wbudowany asembler](../assembler/inline/inline-assembler.md)<br/>
Korzystanie z języka asembler i C++ w **__asm** bloków.

[Obsługa kompilatora COM](../cpp/compiler-com-support.md)<br/>
Odwołanie do klas specyficznych dla Microsoft i globalne funkcje używane do obsługi typów modelu COM.

[Rozszerzenia Microsoft](../cpp/microsoft-extensions.md)<br/>
Rozszerzenia Microsoft do C++.

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)<br/>
Informacje o niestandardowe zachowanie kompilatora Visual C++.

[Witamy z powrotem w C++](welcome-back-to-cpp-modern-cpp.md)<br/>
Omówienie nowoczesnego języka c++, programowanie wskazówki dotyczące pisania bezpiecznych, prawidłowego i efektywnego programów.

## <a name="related-sections"></a>Sekcje pokrewne

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)<br/>
Materiał odniesienia na temat użycia języka Visual C++ do ukierunkowania środowiska uruchomieniowego języka wspólnego.

[Dokumentacja kompilacji w języku C/C++](../build/reference/c-cpp-building-reference.md)<br/>
Opcje kompilatora, opcje konsolidatora i inne narzędzia kompilacji.

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Materiał referencyjny na temat pragm, dyrektyw preprocesora, wstępnie zdefiniowanych makr i preprocesora.

[Biblioteki Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Lista łączy do referencyjnych stron startowych na temat różnych bibliotek Visual C++.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C](../c-language/c-language-reference.md)