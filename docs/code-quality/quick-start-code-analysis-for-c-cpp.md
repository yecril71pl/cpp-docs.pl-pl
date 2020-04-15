---
title: 'Szybki start: analiza kodu C/C++'
description: Uruchom analizę statyczną w kodzie C++ w programie Visual Studio, aby wykryć typowe problemy z kodowaniem i wady.
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370573"
---
# <a name="quickstart-code-analysis-for-cc"></a>Szybki start: analiza kodu C/C++

Można poprawić jakość aplikacji, uruchamiając regularnie analizę kodu na kod C lub C++. Analiza kodu może pomóc w znalezieniu typowych problemów i naruszeń dobrej praktyki programowania. I znajduje wady, które są trudne do wykrycia poprzez testowanie. Jego ostrzeżenia różnią się od błędów kompilatora i ostrzeżenia: wyszukuje wzorce określonego kodu, które są znane powodować problemy. Oznacza to, że kod, który jest prawidłowy, ale nadal może powodować problemy, dla Ciebie lub dla innych osób, które używają kodu.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurowanie zestawów reguł dla projektu

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla nazwy projektu, a następnie wybierz polecenie **Właściwości**.

1. Opcjonalnie na listach **Konfiguracja** i **Platforma** wybierz konfigurację kompilacji i platformę docelową.

1. Aby przeprowadzić analizę kodu za każdym razem, gdy projekt jest budowany przy użyciu wybranej konfiguracji, zaznacz pole wyboru **Włącz analizę kodu na kompilacji.** Analizę kodu można również uruchomić ręcznie, otwierając menu **Analiza,** a następnie wybierając **polecenie Uruchom analizę kodu w** programie *ProjectName* lub **Uruchom analizę kodu w pliku.**

1. Wybierz [zestaw reguł,](using-rule-sets-to-specify-the-cpp-rules-to-run.md) którego chcesz użyć, lub utwórz [niestandardowy zestaw reguł](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Jeśli używasz LLVM/clang-cl, zobacz [Korzystanie z Clang-Tidy w programie Visual Studio,](../code-quality/clang-tidy.md) aby skonfigurować opcje analizy Clang-Tidy.

### <a name="standard-cc-rule-sets"></a>Standardowe zestawy reguł C/C++

Visual Studio zawiera te standardowe zestawy reguł dla kodu macierzystego:

| Zestaw reguł | Opis |
|--|--|
| **Reguły arytmetyczne sprawdzania rdzenia języka C++** | Reguły te wymuszają kontrole związane [z operacjami arytmetycznymi z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **Reguły sprawdzania podstawowych granic języka C++** | Reguły te [wymuszają profil Granic podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile). |
| **Podstawowe reguły klasy sprawdzania języka C++** | Reguły te wymuszają kontrole związane [z klasami z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies). |
| **Reguły sprawdzania współbieżności rdzenia języka C++** | Reguły te wymuszają kontrole związane [z współbieżnością z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency). |
| **Reguły sprawdzania rdzenia języka C++** | Reguły te [wymuszają kontrole związane z const z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). |
| **Reguły deklaracji sprawdzania rdzenia języka C++** | Zasady te wymuszają kontrole związane [z deklaracjami z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces). |
| **Reguły wyliczenia sprawdzania rdzenia języka C++** | Reguły te [wymuszają kontrole związane z wyliczeniami z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). |
| **Reguły eksperymentalne sprawdzania rdzenia języka C++** | Reguły te zbierają pewne kontrole eksperymentalne. Ostatecznie oczekujemy, że te kontrole zostaną przeniesione do innych zestawy reguł lub całkowicie usunięte. |
| **Reguły funkcji sprawdzania rdzenia języka C++** | Reguły te wymuszają kontrole związane [z funkcjami z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions). |
| **Reguły GSL sprawdzania rdzenia języka C++** | Reguły te wymuszają kontrole związane z [biblioteką pomocy technicznej wytycznych z podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). |
| **Reguły okresu istnienia sprawdzania rdzenia języka C++** | Reguły te wymuszają [profil dożywotniego wytycznych podstawowych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). |
| **Reguły wskaźnika sprawdzania podstawowego języka C++** | Reguły te wymuszają kontrole zarządzania zasobami związane z [właścicielem&lt;T&gt; z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Reguły sprawdzania surowego wskaźnika rdzenia języka C++** | Te reguły wymuszają kontrole zarządzania zasobami związane [z surowymi wskaźnikami z podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Podstawowe reguły sprawdzania języka C++** | Reguły te wymuszają podzbiór kontroli z [podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines). Ten zestawy reguł służy do uwzględnienia wszystkich reguł sprawdzania rdzenia języka C++ z wyjątkiem wyliczeń i eksperymentalnych reguł. |
| **Reguły udostępnionego wskaźnika sprawdzania rdzenia języka C++** | Te reguły wymuszają kontrole zarządzania zasobami związane [z typami z semantyką wskaźnika udostępnionego z podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Reguły STL sprawdzania rdzenia języka C++** | Te reguły wymuszają kontrole związane z [standardową biblioteką szablonów języka C++ (STL) z podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib). |
| **Reguły stylu sprawdzania rdzenia języka C++** | Reguły te wymuszają kontrole związane z używaniem [wyrażeń i instrukcji z podstawowych wytycznych C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **Reguły typu sprawdzania rdzenia języka C++** | Reguły te wymuszają [profil typu podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). |
| **C++ Core Sprawdź unikatowe reguły wskaźnika** | Te reguły wymuszają kontrole zarządzania zasobami związane z typami z [unikatową semantyką wskaźnika z podstawowych wytycznych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Reguły sprawdzania współbieżności** | Te reguły wymuszają zestaw win32 sprawdzania wzorca współbieżności w języku C++. |
| **Reguły współbieżności** | Dodaje reguły współbieżności z podstawowych wytycznych języka C++ do **reguł sprawdzania współbieżności**. |
| **Minimalne reguły natywne firmy Microsoft** | Reguły te koncentrują się na najbardziej krytycznych problemów w kodzie macierzystym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Zalecamy uwzględnienie tego zestawu reguł w dowolnym niestandardowym zestawie reguł utworzonym dla projektów natywnych. |
| **Zalecane reguły natywne firmy Microsoft** | Reguły te koncentrują się na najbardziej krytycznych i typowych problemów w kodzie macierzystym. Problemy te obejmują potencjalne luki w zabezpieczeniach i awarie aplikacji. Zalecamy uwzględnienie tego zestawu reguł w dowolnym niestandardowym zestawie reguł utworzonym dla projektów natywnych. Ten usiet jest przeznaczony do pracy z programem Visual Studio Professional edition i nowszym. Zawiera wszystkie reguły w **minimalnych regułach natywnych microsoft**. |

Visual Studio zawiera te standardowe zestawy reguł dla kodu zarządzanego:

| Zestaw reguł | Opis |
|--|--|
| **Podstawowe reguły poprawności firmy Microsoft** | Reguły te koncentrują się na błędach logicznych i typowych błędach popełnionych w użyciu framework API. Dołącz tę regułę ustawioną, aby rozwinąć listę ostrzeżeń zgłaszanych przez minimalne zalecane reguły. |
| **Podstawowe wytyczne dotyczące projektowania firmy Microsoft** | Te reguły koncentrują się na wymuszaniu najlepszych rozwiązań, aby kod był łatwy do zrozumienia i użycia. Dołącz ten zestaw reguł, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najlepsze rozwiązania dotyczące łatwego w utrzymaniu kodu. |
| **Reguły rozszerzonej poprawności firmy Microsoft** | Te reguły rozwiń na podstawowych reguły poprawności, aby zmaksymalizować zgłoszonych błędów użycia logiki i struktury. Dodatkowy nacisk kładzie się na konkretne scenariusze, takie jak com interop i aplikacje mobilne. Należy rozważyć dołączenie tego zestawu reguł, jeśli jeden z tych scenariuszy ma zastosowanie do projektu lub znaleźć dodatkowe problemy w projekcie. |
| **Rozszerzone wytyczne dotyczące projektowania firmy Microsoft** | Reguły te rozszerzają podstawowe reguły wytycznych dotyczących projektowania, aby zmaksymalizować zgłoszone problemy z użytecznością i możliwością konserwacji. Dodatkowy nacisk kładzie się na wytyczne dotyczące nazewnictwa. Należy rozważyć dołączenie tego zestawu reguł, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najwyższe standardy pisania kodu trzymania. |
| **Reguły globalizacji firmy Microsoft** | Reguły te koncentrują się na problemach, które uniemożliwiają poprawne wyświetlanie danych w aplikacji, gdy są używane w różnych językach, ustawieniach regionalnych i kulturach. Dołącz ten zestaw reguł, jeśli aplikacja jest zlokalizowana i/lub zglobalizowana. |
| **Minimalne reguły zarządzane przez firmę Microsoft** | Reguły te koncentrują się na najbardziej krytycznych problemów w kodzie, dla których analiza kodu jest najbardziej dokładne.  Te reguły są małe i są przeznaczone tylko do uruchamiania w limitowanych wersjach programu Visual Studio.  Użyj MinimumRecommendedRules.ruleset z innymi wersjami programu Visual Studio. |
| **Zalecane reguły zarządzane przez firmę Microsoft** | Reguły te koncentrują się na najbardziej krytycznych problemów w kodzie. Problemy te obejmują potencjalne luki w zabezpieczeniach, awarie aplikacji i inne ważne błędy logiki i projektowania. Zalecamy uwzględnienie tego zestawu reguł w dowolnym niestandardowym zestawie reguł utworzonym dla projektów. |
| **Minimalne reguły microsoftu mieszane (C++ /CLR)** | Reguły te koncentrują się na najbardziej krytycznych problemów w projektach języka C++, które obsługują środowisko uruchomieniowe języka wspólnego. Problemy te obejmują potencjalne luki w zabezpieczeniach, awarie aplikacji i inne ważne błędy logiki i projektowania. Zaleca się dołączenie tego zestawu reguł do dowolnego zestawu reguł niestandardowych utworzonych dla projektów języka C++, które obsługują środowisko uruchomieniowe języka wspólnego. |
| **Zalecane reguły microsoft mixed (C++ /CLR)** | Reguły te koncentrują się na najbardziej typowych i krytycznych problemów w projektach języka C++, które obsługują środowisko uruchomieniowe języka wspólnego. Problemy te obejmują potencjalne luki w zabezpieczeniach, awarie aplikacji i inne ważne błędy logiki i projektowania. Ten usiet jest przeznaczony do użytku w wersji Visual Studio Professional i nowszej. |
| **Reguły zabezpieczeń firmy Microsoft** | Ten zestaw reguł zawiera wszystkie reguły zabezpieczeń firmy Microsoft. Dołącz ten zestaw reguł, aby zmaksymalizować liczbę potencjalnych problemów z zabezpieczeniami, które są zgłaszane. |

Aby uwzględnić każdą regułę:

| Zestaw reguł | Opis |
|--|--|
| **Wszystkie reguły firmy Microsoft** | Ten zestaw reguł zawiera wszystkie reguły. Uruchomienie tego zestawu reguł może spowodować dużą liczbę ostrzeżeń. Użyj tego zestawu reguł, aby uzyskać kompleksowy obraz wszystkich problemów w kodzie. To może pomóc zdecydować, które z bardziej skoncentrowanych zestawów reguł są najbardziej odpowiednie do uruchomienia dla projektów. |

## <a name="run-code-analysis"></a>Uruchamianie analizy kodu

Na stronie **Analiza kodu** w oknie dialogowym Właściwości projektu można skonfigurować analizę kodu do uruchamiania przy każdym tworzeniu projektu. Analizę kodu można również uruchomić ręcznie.

Aby przeprowadzić analizę kodu w rozwiązaniu:

- W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w programie Solution**.

Aby przeprowadzić analizę kodu w projekcie:

1. W Eksploratorze rozwiązań wybierz nazwę projektu.

1. W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w** programie Project *Name*.

Aby przeprowadzić analizę kodu w pliku:

1. W Eksploratorze rozwiązań wybierz nazwę pliku.

1. W menu **Kompilacja** wybierz polecenie **Uruchom analizę kodu w pliku** lub naciśnij **klawisze Ctrl+Shift+Alt+F7**.

   Projekt lub rozwiązanie jest kompilowane i analizy kodu uruchamia. Wyniki są wyświetlane w oknie Lista błędów.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu

Okno Lista błędów zawiera listę znalezionych ostrzeżeń analizy kodu. Wyniki są wyświetlane w tabeli. Jeśli więcej informacji jest dostępnych na temat określonego ostrzeżenia, pierwsza kolumna zawiera formant rozszerzania. Wybierz go, aby rozwinąć wyświetlacz, aby uzyskać dodatkowe informacje o problemie. Jeśli to możliwe, analiza kodu wyświetla numery wierszy i logikę analizy, które doprowadziły do ostrzeżenia.

Aby uzyskać szczegółowe informacje na temat ostrzeżenia, w tym możliwe rozwiązania problemu, wybierz identyfikator ostrzeżenia w kolumnie Kod, aby wyświetlić odpowiedni artykuł pomocy online.

Kliknij dwukrotnie ostrzeżenie, aby przenieść kursor do wiersza kodu, który spowodował ostrzeżenie w edytorze kodu programu Visual Studio. Możesz też nacisnąć klawisz Enter na wybranym ostrzeżeniu.

Po zrozumieniu problemu można go rozwiązać w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlane na liście błędów.

## <a name="create-work-items-for-code-analysis-warnings"></a>Tworzenie elementów roboczych dla ostrzeżeń analizy kodu

Funkcja śledzenia elementu pracy służy do rejestrowania błędów z poziomu programu Visual Studio. Aby korzystać z tej funkcji, należy połączyć się z wystąpieniem usługi Azure DevOps Server (dawniej Team Foundation Server).

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Aby utworzyć element roboczy dla co najmniej jednego ostrzeżenia o kodzie C/C++

1. Na liście błędów rozwiń i wybierz ostrzeżenia

1. W menu skrótów z ostrzeżeniami wybierz pozycję **Utwórz element pracy**, a następnie wybierz typ elementu pracy.

1. Visual Studio tworzy pojedynczy element roboczy dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu IDE.

1. Dodaj dodatkowe informacje, a następnie wybierz pozycję **Zapisz element pracy**.

## <a name="search-and-filter-code-analysis-results"></a>Wyniki analizy kodu wyszukiwania i filtrowania

Można wyszukiwać długie listy komunikatów ostrzegawczych i filtrować ostrzeżenia w rozwiązaniach wieloprojektowych.

- **Aby filtrować ostrzeżenia według tytułu lub identyfikatora ostrzeżenia:** Wpisz słowo kluczowe w polu Lista błędów wyszukiwania.

- **Aby filtrować ostrzeżenia według ważności:** Domyślnie komunikatom analizy kodu przypisywana jest ważność **ostrzeżenia**. Ważność jednego lub większej liczby komunikatów można przypisać jako **błąd** w niestandardowym zestawie reguł. W kolumnie **Ważność** **listy błędów**wybierz strzałkę listy rozwijanej, a następnie ikonę filtru. Wybierz **opcję Ostrzeżenie** lub **Błąd,** aby wyświetlić tylko komunikaty, które mają przypisaną odpowiednią ważność. Wybierz **pozycję Wybierz wszystko,** aby wyświetlić wszystkie wiadomości.

## <a name="see-also"></a>Zobacz też

- [Analiza kodu C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
