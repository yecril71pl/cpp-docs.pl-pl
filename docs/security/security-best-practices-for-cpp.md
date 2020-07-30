---
title: Najlepsze praktyki w zakresie zabezpieczeń dla C++
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 12b2db55a393928683e65c8faca49595fbbebc51
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389964"
---
# <a name="security-best-practices-for-c"></a>Najlepsze praktyki w zakresie zabezpieczeń dla C++

Ten artykuł zawiera informacje o narzędziach i wskazówkach dotyczących zabezpieczeń. Korzystanie z nich nie powoduje, że aplikacje nie odporny na ataki, ale sprawiają, że pomyślne ataki są mniejsze.

## <a name="visual-c-security-features"></a>Visual C++ funkcje zabezpieczeń

Te funkcje zabezpieczeń są wbudowane w kompilator i konsolidator języka Microsoft C++:

[`/guard`(Włącz ochronę przepływu sterowania)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Powoduje, że kompilator analizuje przepływ sterowania dla pośrednich celów wywołań w czasie kompilacji, a następnie wstawia kod w celu zweryfikowania obiektów docelowych w czasie wykonywania.

[`/GS`(Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)<br/>
Instruuje kompilator, aby wstawiał kod wykrywania przepełnienia do funkcji, które są zagrożone. Po wykryciu przekroczenia zostanie zatrzymane wykonywanie operacji. Domyślnie ta opcja jest włączona.

[`/SAFESEH`(Obraz ma bezpieczne procedury obsługi wyjątków)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Nakazuje konsolidatorowi dołączenie do obrazu wyjściowego tabeli zawierającej adres każdego programu obsługi wyjątków. W czasie wykonywania system operacyjny używa tej tabeli, aby upewnić się, że są wykonywane tylko wiarygodne programy obsługi wyjątków. Pozwala to zapobiec wykonywaniu obsługi wyjątków, które zostały wprowadzone w ramach złośliwego ataku w czasie wykonywania. Domyślnie ta opcja jest wyłączona.

[`/NXCOMPAT`](../build/reference/nxcompat.md), [ `/NXCOMPAT` (Zgodne z zapobieganie wykonywaniu danych)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) te opcje kompilatora i konsolidatora umożliwiają zachowanie zgodności zapobiegania wykonywaniu danych (DEP). Funkcja DEP chroni procesor przed wykonaniem stron niekodowych.

[`/analyze`(Analiza kodu)](../build/reference/analyze-code-analysis.md)<br/>
Ta opcja kompilatora aktywuje analizę kodu, która zgłasza potencjalne problemy z zabezpieczeniami, takie jak przepełnienie buforu, pamięć niezainicjowana, cofanie odwołania wskaźnika i przecieki pamięci. Domyślnie ta opcja jest wyłączona. Aby uzyskać więcej informacji, zobacz [Analiza kodu dla C/C++ — Omówienie](/cpp/code-quality/code-analysis-for-c-cpp-overview).

[`/DYNAMICBASE`(Użyj losowości układu przestrzeni adresowej)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Ta opcja konsolidatora umożliwia tworzenie obrazu wykonywalnego, który może zostać załadowany w różnych lokalizacjach w pamięci na początku wykonywania. Ta opcja powoduje również, że lokalizacja stosu w pamięci znacznie mniej przewidywalna.

## <a name="security-enhanced-crt"></a>Ulepszone zabezpieczenia — CRT

Biblioteka środowiska uruchomieniowego języka C (CRT) została uzupełniona w celu uwzględnienia bezpiecznych wersji funkcji, które stanowią zagrożenie bezpieczeństwa, na przykład funkcji kopiowania niesprawdzonych `strcpy` ciągów. Ze względu na to, że starsze, niezabezpieczone wersje tych funkcji są przestarzałe, powodują to ostrzeżenia w czasie kompilacji. Zachęcamy do używania bezpiecznych wersji tych funkcji CRT zamiast pomijania ostrzeżeń kompilacji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>Biblioteka SafeInt

[Biblioteka SafeInt](../safeint/safeint-library.md) pomaga zapobiegać przepełnieniu liczby całkowitej oraz innym błędom, które mogą wystąpić, gdy aplikacja wykonuje operacje matematyczne. `SafeInt`Biblioteka zawiera [klasę SafeInt](../safeint/safeint-class.md), [klasę SafeIntException](../safeint/safeintexception-class.md)i kilka [funkcji SafeInt](../safeint/safeint-functions.md).

`SafeInt`Klasa chroni przed przepełnieniem liczby całkowitej i wykorzystaniem dzielenia przez zero. Można jej użyć do obsługi porównań między wartościami różnych typów. Zawiera dwie zasady obsługi błędów. Zasady domyślne są przeznaczone dla `SafeInt` klasy, aby zgłosić `SafeIntException` wyjątek klasy w celu zgłaszania, dlaczego nie można ukończyć operacji matematycznej. Druga zasada dotyczy `SafeInt` klasy, aby zatrzymać wykonywanie programu. Istnieje również możliwość zdefiniowania zasad niestandardowych.

Każda `SafeInt` Funkcja chroni jedną operację matematyczną z powodu błędu możliwego do wykorzystania. Można użyć dwóch różnych rodzajów parametrów bez konwertowania ich na ten sam typ. Aby chronić wiele operacji matematycznych, użyj `SafeInt` klasy.

## <a name="checked-iterators"></a>Zaznaczone iteratory

Sprawdzony iterator wymusza granice kontenera. Domyślnie, gdy sprawdzony iterator jest poza zakresem, generuje wyjątek i zamyka wykonywanie programu. Sprawdzony iterator zapewnia inne poziomy odpowiedzi, które są zależne od wartości przypisanych do preprocesora, takich jak `_SECURE_SCL_THROWS` i `_ITERATOR_DEBUG_LEVEL` . Na przykład, w przypadku `_ITERATOR_DEBUG_LEVEL=2` , sprawdzony iterator zapewnia kompleksowe sprawdzanie poprawności w trybie debugowania, które są udostępniane za pomocą potwierdzeń. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) i [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) .

## <a name="code-analysis-for-managed-code"></a>Analizowanie kodu zarządzanego

Analiza kodu dla kodu zarządzanego, znana również jako FxCop, sprawdza zestawy pod kątem zgodności z zaleceniami dotyczącymi projektowania platformy the.NET Framework. FxCop analizuje kod i metadane w każdym zestawie, aby sprawdzić wady w następujących obszarach:

- Projekt biblioteki

- Lokalizacja

- Konwencje nazewnictwa

- Wydajność

- Zabezpieczenia

## <a name="windows-application-verifier"></a>Weryfikator aplikacji systemu Windows

[Weryfikator aplikacji (narzędzia AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) może pomóc identyfikować potencjalne problemy ze zgodnością aplikacji, stabilnością i zabezpieczeniami.

Narzędzia AppVerifier monitoruje, w jaki sposób aplikacja używa systemu operacyjnego. Monitoruje system plików, rejestr, pamięć i interfejsy API, gdy aplikacja jest uruchomiona, i zaleca poprawki kodu źródłowego w przypadku problemów, które zawiera.

Można użyć narzędzia AppVerifier do:

- Przetestuj potencjalne błędy zgodności aplikacji, które są spowodowane przez typowe błędy programistyczne.

- Przejrzyj aplikację pod kątem problemów związanych z pamięcią.

- Zidentyfikuj potencjalne problemy z zabezpieczeniami w aplikacji.

## <a name="windows-user-accounts"></a>Konta użytkowników systemu Windows

Korzystanie z kont użytkowników systemu Windows należących do grupy Administratorzy uwidacznia deweloperów i--przez rozszerzenie--klientom zagrożeń bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [Uruchamianie jako członek grupy Użytkownicy](running-as-a-member-of-the-users-group.md) i sposób, w [jaki Kontrola konta użytkownika (UAC) wpływa na aplikację](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Wskazówki dotyczące kanałów po stronie wykonywania spekulacyjnego

Aby uzyskać informacje na temat sposobu ułatwiającą i łagodzenia luk w zabezpieczeniach sprzętu kanału po stronie wykonywania w języku C++, zobacz [wskazówki dla deweloperów języka c++ dotyczące spekulacyjnych kanałów po stronie wykonywania](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Zobacz też

<xref:System.Security> <br/>
[Bezpieczeństwo](/dotnet/standard/security/index)<br/>
[Jak kontrola konta użytkownika (UAC) wpływa na aplikację](how-user-account-control-uac-affects-your-application.md)
