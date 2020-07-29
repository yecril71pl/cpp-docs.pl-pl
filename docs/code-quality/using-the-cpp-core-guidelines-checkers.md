---
title: Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 9c36c17e819e954d66833f059fe794ac14898e75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227728"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++

Podstawowe wytyczne dotyczące języka C++ są przenośnym zestawem wytycznych, regułami i najlepszymi rozwiązaniami dotyczącymi kodowania w języku C++ utworzonym przez ekspertów i projektantów języka C++. Program Visual Studio obecnie obsługuje podzbiór tych reguł w ramach narzędzi do analizy kodu dla języka C++. Główne wskazówki sprawdzające podstawowe są instalowane domyślnie w programie Visual Studio 2017 i Visual Studio 2019 i są [dostępne jako pakiet NuGet dla programu Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projekt podstawowe wytyczne dotyczące języka C++

Podstawowe wytyczne dotyczące języka C++, utworzone przez Bjarne'a Stroustrupa i inne, są przewodnikiem bezpiecznego i efektywnego korzystania z nowoczesnego języka C++. Wytyczne podkreślają bezpieczeństwo typu statycznego i bezpieczeństwo zasobów. Identyfikują one sposoby eliminacji lub minimalizowania najbardziej podatnych na błędy części języka, a także sugerują sposób prostszego i bardziej wydajnego wykonywania kodu. Te wytyczne są obsługiwane przez standard C++ Foundation. Aby dowiedzieć się więcej, zobacz dokumentację [podstawowe wytyczne dotyczące języka C++](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)i dostęp do plików projektu dokumentacji podstawowe wytyczne dotyczące języka C++ w witrynie [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz wskazówki dotyczące podstawowe sprawdzanie języka C++ w analizie kodu

Możesz włączyć analizę kodu w projekcie, zaznaczając pole wyboru **Włącz analizę kodu podczas kompilacji** w sekcji **Analiza kodu** okna dialogowego **strony właściwości** dla projektu.

![Strona właściwości dla ustawień ogólnych analizy kodu](media/cppcorecheck_codeanalysis_general.png)

Podzbiór reguł podstawowe sprawdzanie języka C++ jest zawarty w domyślnym, zalecanym przez firmę Microsoft zestawem reguł, który jest uruchamiany domyślnie po włączeniu analizy kodu. Aby włączyć dodatkowe podstawowe reguły sprawdzania, kliknij listę rozwijaną i wybierz zestawy reguł, które chcesz uwzględnić:

![Lista rozwijana dla dodatkowych zestawów reguł podstawowe sprawdzanie języka C++](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Przykłady

Oto przykład niektórych problemów, które można znaleźć w regułach podstawowe sprawdzanie języka C++:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Ten przykład ilustruje kilka ostrzeżeń, które mogą znaleźć reguły podstawowe sprawdzanie języka C++:

- C26494 jest typem reguły. 5: zawsze Inicjuj obiekt.

- C26485 jest zakresem reguł. 3: brak zanikania tablicy do wskaźnika.

- C26481 jest zakresem reguł. 1: nie używaj arytmetyki wskaźnika. Zamiast tego użyj polecenia cmdlet `span`.

Jeśli zestaw reguł analizy kodu podstawowe sprawdzanie języka C++ są instalowane i włączane podczas kompilowania tego kodu, pierwsze dwa ostrzeżenia są wyjściowe, ale trzeci jest pomijany. Oto dane wyjściowe kompilacji z przykładowego kodu:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Podstawowe wytyczne dotyczące języka C++ można ułatwić pisanie lepszych i bezpieczniejszych kodów. Jeśli jednak istnieje wystąpienie, w którym nie należy stosować reguły lub profilu, można je łatwo pominąć bezpośrednio w kodzie. Możesz użyć atrybutu, `gsl::suppress` Aby zachować podstawowe sprawdzanie języka C++ wykrywania i raportowania wszelkich naruszeń reguły w poniższym bloku kodu. Można oznaczyć poszczególne instrukcje, aby pominąć określone reguły. Można nawet pominąć profil całego ograniczenia, pisząc `[[gsl::suppress(bounds)]]` bez uwzględniania określonego numeru reguły.

## <a name="supported-rule-sets"></a>Obsługiwane zestawy reguł

W miarę dodawania nowych reguł do narzędzia podstawowe wytyczne dotyczące języka C++ Checker, liczba ostrzeżeń, które są generowane dla istniejącego kodu, może się zwiększyć. Wstępnie zdefiniowanych zestawów reguł można użyć do filtrowania typów reguł do włączenia.
Tematy referencyjne dotyczące większości reguł znajdują się w sekcji [informacje dotyczące podstawowe sprawdzanie języka C++ programu Visual Studio](code-analysis-for-cpp-corecheck.md).

W programie Visual Studio 2017 w wersji 15,3 obsługiwane są następujące zestawy reguł:

- **Reguły wskaźnika właściciela** wymuszają [operacje sprawdzania zarządzania zasobami powiązane \<T> z właścicielem z podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły const** wymuszają [sprawdzenia związane z wartością stałą z podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Reguły wskaźnika RAW** wymuszają [operacje sprawdzania zarządzania zasobami powiązane ze wskaźnikami nieprzetworzonymi z podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły unikatowego wskaźnika** wymuszają [operacje sprawdzania zarządzania zasobami powiązane z typami z semantyką unikatowego wskaźnika z podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Reguły związane z ograniczeniami** wymuszają [profil ograniczenia podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Reguły typu** wymuszają [Profil typu podstawowe wytyczne dotyczące języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Program Visual Studio 2017 w wersji 15,5**:

- **Reguły klas** Kilka reguł, które koncentrują się na właściwym użyciu specjalnych funkcji składowych i specyfikacji wirtualnych. Jest to podzbiór sprawdzań zalecany dla [klas i hierarchii klas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Reguły współbieżności** Pojedyncza reguła, która przechwytuje nieprawidłowo zadeklarowane obiekty Guard. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące współbieżności](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Reguły deklaracji** Kilka reguł z [wytycznych dotyczących interfejsów](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) , które koncentrują się na sposobie deklarowania zmiennych globalnych.
- **Reguły funkcji** Dwie kontrole, które pomagają w przyjęciu **`noexcept`** specyfikatora. Jest to część wytycznych dotyczących [projektowania i implementacji funkcji czyszczenia](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Reguły wspólnego wskaźnika** W ramach wymuszania wytycznych dotyczących [zarządzania zasobami](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) dodaliśmy kilka reguł specyficznych dla sposobu przekazywania współużytkowanych wskaźników do funkcji lub używanych lokalnie.
- **Reguły stylu** Jedna prosta, ale ważna kontrola, która zakazuje używania instrukcji [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Jest to pierwszy krok ulepszania stylu kodowania i używania wyrażeń i instrukcji w języku C++.

**Program Visual Studio 2017 w wersji 15,6**:

- **Reguły arytmetyczne** Reguły wykrywające [przepełnienie](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)arytmetyczne, [operacje podpisane bez znaku](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) i [manipulowanie bitowe](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Można wybrać ograniczenie ostrzeżeń tylko do jednej lub kilku grup. **Natywne minimalne** i **natywne zalecane** zestawy reguł obejmują reguły podstawowe sprawdzanie języka C++ oprócz innych funkcji szybkiego sprawdzania. Aby wyświetlić dostępne zestawy reguł, Otwórz okno dialogowe właściwości projektu, wybierz pozycję **kod Analysis\General**, Otwórz listę rozwijaną w polu kombi **zestawy reguł** i wybierz **pozycję zaznacz wiele zestawów reguł**. Aby uzyskać więcej informacji o korzystaniu z zestawów reguł w programie Visual Studio, zobacz [Korzystanie z zestawów reguł do określania reguł języka C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

## <a name="macros"></a>Makra

Narzędzie podstawowe wytyczne dotyczące języka C++ Checker zawiera plik nagłówka, który definiuje makra, które ułatwiają pomijanie wszystkich kategorii ostrzeżeń w kodzie:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Te makra odpowiadają zestawom reguł i rozszerzają je na listę wartości ostrzeżeń rozdzielonych spacjami. Korzystając z odpowiednich konstrukcji dyrektywy pragma, można skonfigurować obowiązujący zestaw reguł, które są interesujące dla projektu lub sekcji kodu. W poniższym przykładzie Analiza kodu ostrzega tylko o brakujących modyfikatorach stałych:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atrybuty

Kompilator języka Microsoft C++ ma ograniczoną obsługę atrybutu pomijania GSL. Może służyć do pomijania ostrzeżeń dotyczących wyrażeń i bloków instrukcji wewnątrz funkcji.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Pomiń analizę przy użyciu opcji wiersza polecenia

Zamiast #pragmas można użyć opcji wiersza polecenia na stronie właściwości pliku, aby pominąć ostrzeżenia dla projektu lub pojedynczego pliku. Na przykład, aby wyłączyć C26400 ostrzegawczy dla pliku:

1. Kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań**

1. Wybierz **właściwości | C/C++ | Wiersz polecenia**

1. W oknie **Opcje dodatkowe** Dodaj `/wd26400` .

Można użyć opcji wiersza polecenia, aby tymczasowo wyłączyć wszystkie analizy kodu dla pliku przez określenie `/analyze-` . Spowoduje to wygenerowanie ostrzeżenia *D9025 przesłanianie "/ANALYZE" z "/ANALYZE-"*, co przypomina ponowne włączenie analizy kodu później.

## <a name="enable-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a>Włącz narzędzie podstawowe wytyczne dotyczące języka C++ Checker dla określonych plików projektu

Czasami warto skorzystać z ukierunkowanej analizy kodu i nadal używać środowiska IDE programu Visual Studio. Następujący przykładowy scenariusz może być używany w przypadku dużych projektów do zapisywania czasu kompilacji i ułatwiający filtrowanie wyników:

1. W powłoce poleceń Ustaw `esp.extension` `esp.annotationbuildlevel` zmienne środowiskowe i.
1. Aby odziedziczyć te zmienne, Otwórz program Visual Studio z poziomu powłoki poleceń.
1. Załaduj projekt i otwórz jego właściwości.
1. Włącz analizę kodu, wybierz odpowiednie zestawy reguł, ale nie włączaj rozszerzeń analizy kodu.
1. Przejdź do pliku, który chcesz analizować za pomocą narzędzia podstawowe wytyczne dotyczące języka C++ Checker i otwórz jego właściwości.
1. Wybierz **Opcje linii \Command C/C++** i Dodaj`/analyze:plugin EspXEngine.dll`
1. Wyłącz używanie prekompilowanego nagłówka (**nagłówki \Precompiled C/C++**). Jest to konieczne, ponieważ aparat rozszerzeń może próbować odczytać informacje wewnętrzne z prekompilowanego nagłówka (PCH); Jeśli PCH skompilowane z użyciem domyślnych opcji projektu, nie będzie zgodny.
1. Ponownie skompiluj projekt. Wspólne testy szybkie są uruchamiane na wszystkich plikach. Ponieważ narzędzie podstawowe wytyczne dotyczące języka C++ Checker nie jest domyślnie włączone, powinno być uruchamiane tylko na pliku, który jest skonfigurowany do korzystania z niego.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak używać narzędzia podstawowe wytyczne dotyczące języka C++ Checker poza programem Visual Studio

Możesz użyć podstawowe wytyczne dotyczące języka C++ checks w zautomatyzowanych kompilacjach.

### <a name="msbuild"></a>MSBuild

Narzędzie sprawdzania kodu natywnego (wstępnie Fast) jest zintegrowane ze środowiskiem MSBuild przez pliki niestandardowych elementów docelowych. Możesz użyć właściwości projektu, aby je włączyć, i dodać moduł sprawdzania podstawowe wytyczne dotyczące języka C++ (który jest oparty na szybkim przeniesieniu):

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Przed zaimportowaniem pliku Microsoft. cpp. targets należy dodać te właściwości. Można wybrać konkretne zestawy reguł lub utworzyć niestandardowy zestaw reguł lub użyć domyślnego zestawu reguł, który zawiera inne szybkie testy.

Narzędzie sprawdzania rdzenia C++ można uruchomić tylko dla określonych plików, korzystając z tego samego podejścia jak [opisane wcześniej](#corecheck_per_file), ale przy użyciu plików programu MSBuild. Zmienne środowiskowe można ustawić za pomocą `BuildMacro` elementu:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Jeśli nie chcesz modyfikować pliku projektu, możesz przekazać właściwości w wierszu polecenia:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projekty inne niż MSBuild

W przypadku korzystania z systemu kompilacji, który nie korzysta z programu MSBuild, nadal można uruchomić narzędzie sprawdzania, ale należy zapoznać się z niektórymi wewnętrznymi konfiguracją aparatu analizy kodu. Te wewnętrzne nie są gwarantowane w przyszłości.

Należy ustawić kilka zmiennych środowiskowych i użyć odpowiednich opcji wiersza polecenia dla kompilatora. Lepiej jest używać środowiska "natywnych narzędzi wiersza polecenia", dzięki czemu nie trzeba wyszukiwać określonych ścieżek dla kompilatora, zawierać katalogów itp.

- **Zmienne środowiskowe**
  - `set esp.extensions=cppcorecheck.dll`Oznacza to, że aparat załaduje moduł podstawowe wytyczne dotyczące języka C++.
  - `set esp.annotationbuildlevel=ignore`Spowoduje to wyłączenie logiki, która przetwarza adnotacje SAL. Adnotacje nie wpływają na analizę kodu w module podstawowe wytyczne dotyczące języka C++ Checker, ale czas ich przetwarzania (czasami długi czas). To ustawienie jest opcjonalne, ale zdecydowanie zalecane.
  - `set caexcludepath=%include%`Zdecydowanie zalecamy wyłączenie ostrzeżeń, które są uruchamiane w standardowych nagłówkach. W tym miejscu możesz dodać więcej ścieżek, na przykład ścieżkę do wspólnych nagłówków w projekcie.

- **Opcje wiersza polecenia**
  - `/analyze`Włącza analizę kodu (należy rozważyć także użycie/analyze: Only i/analyze: Quiet).
  - `/analyze:plugin EspXEngine.dll`Ta opcja ładuje aparat rozszerzeń analizy kodu do przodu. Ten aparat z kolei ładuje narzędzie podstawowe wytyczne dotyczące języka C++ Checker.

## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki podstawowej pomocy technicznej

Podstawowa Biblioteka pomocy technicznej została zaprojektowana w celu ułatwienia przestrzegania podstawowych wytycznych. GSL zawiera definicje, które umożliwiają zamianę konstrukcji podatnych na błędy z bezpieczniejszymi alternatywami. Na przykład można zastąpić `T*, length` parę parametrów `span<T>` typem. GSL jest dostępny pod adresem [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Biblioteka jest open source, dzięki czemu można przeglądać źródła, wprowadzać komentarze lub współtworzyć. Projekt można znaleźć pod adresem [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a>Używanie wytycznych podstawowe sprawdzanie języka C++ w projektach programu Visual Studio 2015

W przypadku korzystania z programu Visual Studio 2015 zestawy reguł analizy kodu podstawowe sprawdzanie języka C++ nie są instalowane domyślnie. Przed włączeniem podstawowe sprawdzanie języka C++ narzędzia do analizy kodu w programie Visual Studio 2015 należy wykonać kilka dodatkowych kroków. Firma Microsoft zapewnia pomoc techniczną dla projektów programu Visual Studio 2015 przy użyciu pakietu NuGet. Pakiet ma nazwę Microsoft. CppCoreCheck i jest dostępny pod adresem [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Ten pakiet wymaga co najmniej programu Visual Studio 2015 z aktualizacją Update 1.

Pakiet instaluje również inny pakiet jako zależność, tylko w przypadku podstawowej biblioteki obsługi (GSL). GSL jest również dostępna w witrynie GitHub pod adresem [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

Ze względu na sposób ładowania reguł analizy kodu należy zainstalować pakiet NuGet Microsoft. CppCoreCheck w każdym projekcie C++, który ma być sprawdzany w programie Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Aby dodać pakiet Microsoft. CppCoreCheck do projektu w programie Visual Studio 2015

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, do którego chcesz dodać pakiet. Wybierz pozycję **Zarządzaj pakietami NuGet** , aby otworzyć **Menedżera pakietów NuGet**.

1. W oknie **Menedżer pakietów NuGet** Wyszukaj ciąg Microsoft. CppCoreCheck.

    ![Okno Menedżera pakietów NuGet zawiera pakiet CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

1. Wybierz pakiet Microsoft. CppCoreCheck, a następnie wybierz przycisk **Instaluj** , aby dodać reguły do projektu.

   Pakiet NuGet dodaje do projektu dodatkowy plik MSBuild *. targets* , który jest wywoływany po włączeniu analizy kodu dla projektu. Ten plik *targets* dodaje reguły podstawowe sprawdzanie języka C++ jako dodatkowe rozszerzenie narzędzia do analizy kodu programu Visual Studio. Po zainstalowaniu pakietu można użyć okna dialogowego strony właściwości, aby włączyć lub wyłączyć reguły wydane i eksperymentalne.

## <a name="see-also"></a>Zobacz także

- [Informacje dotyczące podstawowe sprawdzanie języka C++ programu Visual Studio](code-analysis-for-cpp-corecheck.md)
