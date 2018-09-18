---
title: Dokumentacja języka C++ | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 708db2b20cdbbe2e322075789f64433ff70612a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025519"
---
# <a name="c-language-reference"></a>Materiał referencyjny na temat języka C++

To źródło odniesienia wyjaśnia sposób implementacji C++ w Microsoft Visual C++. Organizacja jest oparta na *The Annotated C++ Reference Manual* autorstwa Margaret Ellis i Bjarne'a Stroustrupa oraz na ANSI/ISO C++ Międzynarodowy Standard (ISO/IEC FDIS 14882). Implementacje funkcji języka C++ specyficzne dla Microsoft są uwzględnione.

Omówienie rozwiązania w zakresie programowania nowoczesnym języku C++, zobacz [powitalnej zwrotnie do C++](welcome-back-to-cpp-modern-cpp.md).

Zobacz następujące tabele, aby szybko znaleźć słowo kluczowe lub operator:

- [Słowa kluczowe języka C++](../cpp/keywords-cpp.md)

- [Operatory języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>W tej sekcji

[Konwencje leksykalne](../cpp/lexical-conventions.md) podstawowe elementy leksykalne w programie C++: tokeny, komentarze, operatory, słowa kluczowe, przerywniki języka, literały. A także translacja pliku, pierwszeństwo/łączność operatorów.

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md) zakres, powiązanie, uruchamiania programu i zakończenia, klasy magazynu i typów.

[Konwersje standardowe](../cpp/standard-conversions.md) wpisz konwersje między typami wbudowanymi lub "podstawowymi". Ponadto konwersje arytmetyczne i konwersje między wskaźnikiem, odwołaniem i typem wskaźnika do elementu członkowskiego.

[Operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md) operatory w języku C++.

[Wyrażenia](../cpp/expressions-cpp.md) odwoływać się do typów wyrażeń, semantyki wyrażeń, tematów dotyczących operatorów, rzutowania i operatorów rzutowania, informacje typu run-time.

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md) technika programowania, która niejawnie definiuje klasę obiektu funkcyjnego i tworzy obiekt funkcyjny tego typu klasy.

[Instrukcje](../cpp/statements-cpp.md) wyrażenia, instrukcji o wartości null, złożone, wyboru, iteracji, skoku i deklaracji.

[Deklaracje i definicje](declarations-and-definitions-cpp.md) specyfikatory klasy magazynowej, definicje funkcji, inicjalizacje, wyliczenia, **klasy**, **struktury**, i **Unii** deklaracje i **typedef** deklaracji. Ponadto **wbudowane** funkcji **const** — słowo kluczowe, przestrzenie nazw.

[Klas, struktur i Unii](../cpp/classes-and-structs-cpp.md) wprowadzenie do klas, struktur i Unii. Ponadto funkcje Członkowskie, specjalnych funkcji składowych, składowe danych, pola bitowe, **to** wskaźnika, klasy zagnieżdżone.

[Klasy pochodne](../cpp/inheritance-cpp.md) dziedziczenie pojedyncze lub wielokrotne, **wirtualnego** funkcje, wiele klas bazowych, **abstrakcyjne** klasy, reguły zakresu. Ponadto **__super** i **__interface** słów kluczowych.

[Kontrola dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) kontrolowanie dostępu do składowych klasy: **publicznych**, **prywatnej**, i **chronione** słów kluczowych. Funkcje i klasy zaprzyjaźnione.

[Przeciążanie](operator-overloading.md) przeciążone operatory, zasady dotyczące przeciążania operatorów.

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) Obsługa wyjątków języka C++, wyjątków strukturalnych (SEH) obsługi, słowa kluczowe używane w pisaniu instrukcji obsługi wyjątków.

[Potwierdzanie i komunikaty User-Supplied](../cpp/assertion-and-user-supplied-messages-cpp.md) 
 `#error` dyrektywy, **static_assert** — słowo kluczowe, `assert` makra.

[Szablony](../cpp/templates-cpp.md) specyfikacje szablonu, funkcja szablonów, szablony klas **typename** — słowo kluczowe, szablony a makra, szablony i inteligentne wskaźniki.

[Obsługa zdarzeń](../cpp/event-handling.md) deklarowanie zdarzeń i programów obsługi zdarzeń.

[Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md) Modyfikatory specyficzne dla Microsoft C++. Pamięć adresowania, Konwencje wywoływania, **"naked"** funkcje, rozszerzone atrybuty klasy magazynu (**__declspec**), **__w64**.

[Asembler wbudowany](../assembler/inline/inline-assembler.md) przy użyciu języka asembler i C++ w **__asm** bloków.

[Obsługa kompilatora COM](../cpp/compiler-com-support.md) odwołanie do klasy specyficzne dla firmy Microsoft i globalne funkcje używane do obsługi typów modelu COM.

[Microsoft Extensions](../cpp/microsoft-extensions.md) rozszerzeń Microsoft C++.

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md) informacji na temat niestandardowe zachowanie kompilatora Visual C++.

[Witamy z powrotem na C++](welcome-back-to-cpp-modern-cpp.md) Przegląd nowoczesnym programowaniu C++ wskazówki dotyczące pisania bezpiecznych, prawidłowego i efektywnego programów.

## <a name="related-sections"></a>Sekcje pokrewne

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md) odwoływać się do materiału na temat korzystania z języka Visual C++ na docelowe środowisko uruchomieniowe języka wspólnego.

[Odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md) kompilatora opcje, opcje konsolidatora i inne narzędzia do kompilacji.

[C/C++ Preprocessor Reference](../preprocessor/c-cpp-preprocessor-reference.md) odwołania materiał na pragm, dyrektyw preprocesora, wstępnie zdefiniowanych makr i preprocesora.

[Biblioteki języka Visual C++](../standard-library/cpp-standard-library-reference.md) listy łączy do referencyjnych stron startowych na temat różnych bibliotek Visual C++.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C](../c-language/c-language-reference.md)