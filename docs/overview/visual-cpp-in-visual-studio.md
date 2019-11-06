---
title: Język C++ w programie Visual Studio
description: Wizualizacja C++ to nazwa kompilatora firmy Microsoft C++ , edytora kodu i narzędzi pokrewnych w środowisku IDE programu Visual Studio. Użyj wizualizacji C++ do tworzenia programów dla systemów Windows, Linux, Android i iOS.
ms.date: 07/02/2019
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ea047aca90b03179c0a39cb653e0b9bc08306c64
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626218"
---
# <a name="c-in-visual-studio"></a>Język C++ w programie Visual Studio

> [!NOTE]
> Ta dokumentacja dotycząca deweloperów ma zastosowanie do programu Visual Studio 2015 lub nowszego. Użyj selektora wersji w lewym górnym rogu strony, aby dopasować się do używanej wersji programu Visual Studio.
>
> Jeśli szukasz pakietu redystrybucyjnego C++ Visual w taki sposób, aby można było uruchomić program, przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/download/) i wprowadź **wizualizację C++**  w polu wyszukiwania.

Program Microsoft C++Visual, zwykle skrócony do C++ wizualizacji lub MSVC, jest nazwą dla C++narzędzi deweloperskich i bibliotek języka asemblera, dostępnych w ramach programu Visual Studio w systemie Windows. Te narzędzia i biblioteki pozwalają tworzyć aplikacje platforma uniwersalna systemu Windows (platformy UWP), natywne aplikacje pulpitu i serwera systemu Windows, biblioteki i aplikacje dla wielu platform, które działają w systemach Windows, Linux, Android i iOS, a także zarządzane aplikacje i biblioteki korzystające z platformy .NET Architektura. Możesz użyć wizualizacji C++ , aby napisać coś z prostych aplikacji konsolowych do najbardziej zaawansowanych i złożonych aplikacji dla komputerów z systemem Windows, ze sterowników urządzeń i składników systemu operacyjnego do gier wieloplatformowych dla urządzeń przenośnych oraz od najmniejszych urządzeń IoT do obliczeń o wysokiej wydajności na serwerze w chmurze platformy Azure.

Program Visual Studio 2015, 2017 i 2019 można zainstalować obok siebie. Do edytowania i kompilowania programów przy użyciu zestawu narzędzi z programu Visual Studio 2015 (wersji 140) i Visual Studio 2017 (najnowsze 141) można użyć programu Visual Studio 2019 (zestawu narzędzi kompilatora v142).

## <a name="whats-new-and-conformance-history"></a>Historia informacji o nowościach i zgodności

[Co nowego C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
Dowiedz się, co nowego w programie Visual Studio.

[Co nowego C++ w programie Visual Studio 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Dowiedz się, co nowego C++ w programie dla każdej wersji programu Visual Studio od 2003 do 2015.

[Ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md)<br/>
Dowiedz C++ się więcej na temat ulepszeń zgodności w programie Visual Studio.

[Tabela C++ zgodności języka firmy Microsoft](visual-cpp-language-conformance.md)<br/>
Lista Stanów zgodności według funkcji w kompilatorze MSVC C++ .

[Visual C++ — historia zmian w latach 2003–2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
Dowiedz się więcej o istotnych zmianach w poprzednich wersjach.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Zainstaluj program Visual Studio i Uaktualnij go ze starszych wersji

[Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md)<br/>
Pobierz program Visual Studio 2017 lub Visual Studio 2019 i Zainstaluj zestaw C++ narzędzi wizualnych.

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
Wskazówki dotyczące przenoszenia kodu i uaktualniania projektów do programu Visual Studio 2015 lub nowszego, aby wykorzystać lepszą zgodność kompilatora z C++ normą, a także znacznie ulepszone czasy kompilacji i funkcje zabezpieczeń, takie jak Spectre.

[Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
Poznaj różne wersje Visual Studio.

[Obsługiwane platformy](supported-platforms-visual-cpp.md)<br/>
Dowiedz się, które platformy są obsługiwane.

## <a name="learn-c"></a>Dowiedz sięC++

[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
Dowiedz się więcej C++ o nowoczesnych technikach programistycznych opartych na języku c++ 11 i nowszych, które umożliwiają pisanie szybkiego i bezpiecznego kodu oraz uniknięcie wielu pułapek programowania w stylu języka C.

[StandardowaC++](https://isocpp.org/)<br/>
Dowiedz się o języku C++, uzyskaj omówienie nowoczesnego języka C++, znajdź łącza do książek, artykułów, rozmów i imprez

[Poznaj wizualizacjęC++](../build/vscpp-step-1-create.md)<br/>
Rozpocznij naukę języka C++.

[Przykłady Visual C++](visual-cpp-samples.md)<br/>
Informacje dotyczące przykładów.

## <a name="c-development-tools"></a>C++Narzędzia programistyczne

[Omówienie C++ programowania w programie Visual Studio](overview-of-cpp-development.md)<br/>
Jak za pomocą środowiska IDE programu Visual Studio tworzyć projekty, edytować kod, łączyć się z bibliotekami, kompilować, debugować, tworzyć testy jednostkowe, przeprowadzać analizę statyczną, wdrażać i wykonywać inne czynności.

[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
Jak tworzyć i konfigurować projekty programu Visual C++ Studio, projekty CMAKE oraz inne rodzaje projektów z użyciem kompilatora MSVC i opcji konsolidatora.

[Pisanie i Refaktoryzacja C++ kodu](../ide/writing-and-refactoring-code-cpp.md)<br/>
Jak używać funkcji produktywności w C++ edytorze do refaktoryzacji, nawigowania, zrozumienia i pisania kodu.

[Debugowanie kodu natywnego](/visualstudio/debugger/debugging-native-code)<br/>
Użyj debugera programu Visual Studio z C++ projektami.

[Analiza kodu dla języka CC++ /przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)<br/>
Użyj adnotacji SAL lub C++ głównych wytycznych do sprawdzania, aby przeprowadzić analizę statyczną.

[Zapisz testy jednostkowe dla CC++ /w Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp)<br/>
Tworzenie testów jednostkowych przy użyciu struktury testów jednostkowych C++firmy Microsoft dla, Google test, zwiększanie. Testowanie lub narzędzia ctest.

## <a name="write-applications-in-c"></a>Zapisz aplikacje wC++

[Aplikacje uniwersalne systemu Windows (C++)](../cppcx/universal-windows-apps-cpp.md)<br/>
Znajdź przewodniki i treści referencyjne w Centrum deweloperów systemu Windows. Aby uzyskać informacje na temat tworzenia aplikacji platformy UWP, zobacz [wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide) i [Tworzenie pierwszej aplikacji platformy UWP przy C++użyciu ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)programu.

[Aplikacje klasyczne (C++)](../windows/desktop-applications-visual-cpp.md)<br/>
Dowiedz się, jak tworzyć C++ tradycyjne natywne aplikacje klasyczne dla systemu Windows.

[Programowanie .NET w języku C++/interfejsie wiersza polecenia](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Dowiedz się, jak tworzyć biblioteki DLL, które C++ umożliwiają współdziałanie programów natywnych i C# .NET pisanych w językach takich jak lub Visual Basic.

[Programowanie dla systemu Linux](../linux/index.md)<br/>
Użyj środowiska IDE programu Visual Studio, aby wykonać kod i wdrożyć go na zdalnej maszynie z systemem Linux na potrzeby kompilacji za pomocą programu w zatoce.

[Tworzenie C/C++ dll w Visual Studio](../build/dlls-in-visual-cpp.md)<br/>
Poznaj sposób używania Win32, ATL i MFC do tworzenia bibliotek DLL dla pulpitu systemu Windows, poznaj informacje o sposobach kompilowania i rejestrowania biblioteki DLL.

[Programowanie równoległe](../parallel/parallel-programming-in-visual-cpp.md)<br/>
Dowiedz się, jak używać biblioteki wzorców równoległych, C++ AMP, OpenMP i innych funkcji, które są związane z wielowątkowością w systemie Windows.

[Najlepsze rozwiązania w zakresie zabezpieczeń](../security/security-best-practices-for-cpp.md)<br/>
Dowiedz się, jak chronić aplikacje przed złośliwym kodem i bezprawnym użyciem.

[Programowanie w chmurze i sieci Web](../cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
W C++programie dostępnych jest kilka opcji nawiązywania połączenia z siecią Web i chmurą.

[Dostęp do danych](../data/data-access-in-cpp.md)<br/>
Połącz się z bazami danych za pomocą ODBC i OLE DB.

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
Dowiedz się więcej na temat pracy z różnymi formatami tekstu i ciągów oraz kodowaniem dla rozwoju lokalnego i międzynarodowego.

## <a name="languages-reference"></a>Dokumentacja języków

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)

[Dokumentacja języka C](../c-language/c-language-reference.md)

[Funkcje wewnętrzne kompilatora i język asemblera](../intrinsics/compiler-intrinsics-and-assembly-language.md)

## <a name="c-libraries-in-visual-studio"></a>C++Biblioteki w programie Visual Studio

Poniższe sekcje zawierają informacje dotyczące różnych języków C i C++ bibliotek, które znajdują się w programie Visual Studio.

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)<br/>
Obejmuje alternatywy o zwiększonym bezpieczeństwie dla funkcji, które są znane ze stwarzania problemów dotyczących bezpieczeństwa.

[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
Biblioteka C++ standardowa.

[Biblioteka aktywnych szablonów (Active Template Library — ATL)](../atl/atl-com-desktop-components.md)<br/>
Obsługa składników i aplikacji modelu COM.

[Biblioteki Microsoft Foundation Class (MFC)](../mfc/mfc-desktop-applications.md)<br/>
Wsparcie dla tworzenia aplikacji pulpitu, mających interfejs użytkownika tradycyjny lub w stylu pakietu Office.

[Biblioteka równoległych wzorców (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Algorytmy asynchroniczne i równoległe, wykonywane przez CPU.

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
Duże równoległe algorytmy, wykonywane przez GPU.

[Biblioteka szablonów środowisko wykonawcze systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
Aplikacje i składniki platforma uniwersalna systemu Windows (platformy UWP).

[Programowanie .NET w języku C++/interfejsie wiersza polecenia](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Programowanie dla wspólnego środowiska czasu wykonywania (common language runtime — CLR).

## <a name="third-party-open-source-c-libraries"></a>Biblioteki Open Source C++ innych firm

Międzyplatformowe narzędzie wiersza polecenia **vcpkg** znacznie upraszcza odnajdywanie i instalację bibliotek typu open source o wysokiej C++ 900. Zobacz [vcpkg: C++ Menedżer pakietów dla systemu Windows](../build/vcpkg.md).

## <a name="feedback-and-community"></a>Opinie i społeczność

[Zgłaszanie problemu z zestawem narzędzi Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
Dowiedz się, jak tworzyć efektywne raporty o błędach względem zestawu narzędzi wizualnych C++ (kompilatora, konsolidatora i inne narzędzia) oraz jak przesłać raport.

[ C++ Blog zespołu firmy Microsoft](https://devblogs.microsoft.com/cppblog/)<br/>
Dowiedz się więcej na temat nowych funkcji i najnowszych informacji od deweloperów C++ narzędzi w programie Visual Studio.

[Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)<br/>
Dowiedz się, jak uzyskać pomoc, zgłaszać błędy i sugestie dotyczące Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C](../c-language/c-language-reference.md)
- [Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)
- [Funkcje wewnętrzne kompilatora i język asemblera](../intrinsics/compiler-intrinsics-and-assembly-language.md)
