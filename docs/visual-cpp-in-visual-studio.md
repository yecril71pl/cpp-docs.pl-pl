---
title: Visual C++ w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unmanaged code, C++
- development environment, Visual C++
- unmanaged code
- Visual C++
- Visual C++, reference
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fecc7f821bec90321095130fb21147d7227685c
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="visual-c-in-visual-studio"></a>Visual C++ w programie Visual Studio

Visual Studio 2017 programowania języka i programowanie narzędzia ułatwiają tworzenie natywnych aplikacji uniwersalnych systemu Windows, natywnych aplikacji stacjonarnych i serwerów bibliotek i platform, uruchomionymi na Android i iOS, a także systemu Windows i zarządzane aplikacje, które są uruchamiane w programie .NET Struktura.

**Kto jest tej dokumentacji?**

Ta zawartość jest dla deweloperów języka C++, którzy pisania programów.

- Jeśli szukasz określonego pakietu redystrybucyjnego C++ i składniki wykonawcze tak, aby uruchomić program, przejdź do [Microsoft](http://www.microsoft.com/) witryny sieci Web, a następnie wprowadź **Visual C++ Redistributable** w polu wyszukiwania. Pobierz i zainstaluj pakiet redystrybucyjny architektura komputera (na przykład x64 Jeśli używasz 64-bitowego systemu Windows) i wersji programu Visual C++, które są potrzebne. 

- Jeśli szukasz wprowadzenie do pojęcia dotyczące programowania C++, przejdź do jednej z wielu witryn sieci Web, które oferują tej zawartości lub uzyskaj kopię [programowania — zasady i praktyki przy użyciu C++ (wydanie)](http://stroustrup.com/Programming/) przez odłożenie c++, Bjarne Stroustrup. Zawartość Visual C++ przyjęto założenie, że masz już podstawowa znajomość języka C++.

- Jeśli szukasz kompilatora Visual C++, należy pobrać płatną czy bezpłatna wersja programu Visual Studio z [https://www.visualstudio.com/](https://www.visualstudio.com/).

## <a name="general-information-about-visual-c"></a>Ogólne informacje o Visual C++

[Nowości w języku Visual C++](what-s-new-for-visual-cpp-in-visual-studio.md)  
Dowiedz się, co nowego wprowadziliśmy w Visual C++.

[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md)  
Więcej informacji na temat ulepszeń zgodność języka C++ w programie Visual Studio 2017 r.

[Visual zgodność języka C++](visual-cpp-language-conformance.md)  
Lista stanu zgodności przez funkcję w programie Visual C++.

[Visual C++ — historia zmian w latach 2003–2015](porting/visual-cpp-change-history-2003-2015.md)  
Więcej informacji na temat najważniejszych zmian w poprzednich wersjach.

[Zapraszamy ponownie do języka C++](cpp/welcome-back-to-cpp-modern-cpp.md)  
Więcej informacji na temat modern C++ programowania techniki na podstawie języka C ++ 11 i C ++ 14, które umożliwiają szybkie, zapisać bezpiecznego kodu i uniknąć wiele problemów programowania w języku C-style.

[Zgłaszanie problemu z zestawem narzędzi Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)  
 Informacje o sposobie tworzenia raportów skuteczne błąd przed zestaw narzędzi Visual C++ (kompilatora, konsolidatora i inne narzędzia) i sposobów, aby przesłać raport.

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](porting/visual-cpp-porting-and-upgrading-guide.md)  
Wskazówki dotyczące przenoszenia kodu i uaktualnianie projektów dla języka Visual C++ w Visual Studio 2017 r, łącznie z Eksportowanie kodu C++ do systemu Windows 10 i platformy uniwersalnej systemu Windows.

[Blog zespołu usługi Visual C++](http://blogs.msdn.com/b/vcblog/)  
 Dowiedz się więcej na temat nowych funkcji i najnowsze informacje z deweloperzy [!INCLUDE[vcprvc](build/includes/vcprvc_md.md)].

[Pobieranie programu Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=235233)  
Pobierz Visual C++.

[Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)  
Poznaj różne wersje Visual Studio.

[Obsługiwane platformy](supported-platforms-visual-cpp.md)  
Dowiedz się, które platformy są obsługiwane.

[Przykłady Visual C++](visual-cpp-samples.md)  
Informacje dotyczące przykładów.

[Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)  
Dowiedz się, jak uzyskać pomoc, zgłaszać błędy i sugestie dotyczące Visual Studio.

## <a name="writing-applications-in-c"></a>Pisanie aplikacji w języku C++

[Aplikacje uniwersalne systemu Windows](windows/universal-windows-apps-cpp.md)  
Znajdź przewodniki i treści referencyjne w Centrum deweloperów systemu Windows. Informacje dotyczące opracowywania aplikacji ze Sklepu Windows, temacie [deweloperów Sklepu Windows przy użyciu programu Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=248364) i [plan dla Sklepu Windows za pomocą języka C++](http://go.microsoft.com/fwlink/p/?LinkId=244654).

[Aplikacje klasyczne (Visual C++)](windows/desktop-applications-visual-cpp.md)  
Dowiedz się o sposobie tworzenia aplikacji pulpitu, które mają pętle komunikatów i wywołania zwrotne.

[Biblioteki DLL w programie Visual C++](build/dlls-in-visual-cpp.md)  
Poznaj sposób używania Win32, ATL i MFC do tworzenia bibliotek DLL dla pulpitu systemu Windows, poznaj informacje o sposobach kompilowania i rejestrowania biblioteki DLL.

[Programowanie równoległe](parallel/parallel-programming-in-visual-cpp.md)  
Dowiedz się, jak używać biblioteki wzorców równoległych, C++ AMP, OpenMP i innych funkcji, które są związane z wielowątkowością w systemie Windows.

[Najlepsze rozwiązania](security/security-best-practices-for-cpp.md)  
Dowiedz się, jak chronić aplikacje przed złośliwym kodem i bezprawnym użyciem.

[Chmury i sieci Web programowania](cloud/cloud-and-web-programming-in-visual-cpp.md)  
W języku C++ masz kilka opcji łączenia się z sieci web i chmury.

[Dostęp do danych](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b)  
Połączenie z bazami danych za pomocą ODBC i innych technologii dostępu do bazy danych.

[Tekst i ciągi](text/text-and-strings-in-visual-cpp.md)  
Więcej informacji na temat pracy z inny tekst i formaty ciągu i kodowanie dla rozwoju lokalnych i międzynarodowe.

## <a name="c-development-tools"></a>Narzędzia do programowania C++

Aby dowiedzieć się o sposobie tworzenia projektów, pracować z plikami kodu źródłowego, łącze do biblioteki, kompilowania, debugowania, profilu, wdrażanie i więcej, zobacz [IDE i narzędzia deweloperskie](ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="c-language-reference"></a>Dokumentacja języka C++

Aby uzyskać informacje na temat języka C++, zobacz [dokumentacja języka C++](cpp/cpp-language-reference.md).

Informacje o preprocesora języka C++, zobacz [odwołania preprocesora języka C/C++](preprocessor/c-cpp-preprocessor-reference.md).

## <a name="c-libraries-in-visual-studio"></a>Biblioteki języka C++ w programie Visual Studio

Poniższe sekcje zawierają informacje o różnych biblioteki języka C++, które są dołączone do programu Visual C++.

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](c-runtime-library/c-run-time-library-reference.md)  
Obejmuje alternatywy o zwiększonym bezpieczeństwie dla funkcji, które są znane ze stwarzania problemów dotyczących bezpieczeństwa.

[Standardowa biblioteka C++](standard-library/cpp-standard-library-reference.md)  
Standardowa biblioteka C++.

[Biblioteka aktywnych szablonów (Active Template Library — ATL)](atl/atl-com-desktop-components.md)  
Wsparcie dla składników COM i aplikacji.

[Biblioteki Microsoft Foundation Class (MFC)](mfc/mfc-desktop-applications.md)  
Wsparcie dla tworzenia aplikacji pulpitu, mających interfejs użytkownika tradycyjny lub w stylu pakietu Office.

[Biblioteka równoległych wzorców (PPL)](parallel/concrt/parallel-patterns-library-ppl.md)  
Algorytmy asynchroniczne i równoległe, wykonywane przez CPU.

[C++ AMP (C++ Accelerated Massive Parallelism)](parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
Duże równoległe algorytmy, wykonywane przez GPU.

[Biblioteka szablonów środowiska wykonawczego systemu Windows (WRL)](http://msdn.microsoft.com/library/windows/apps/hh438466.aspx)  
[!INCLUDE[win8_appname_long](build/includes/win8_appname_long_md.md)]aplikacje i składniki.

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
Programowanie dla wspólnego środowiska czasu wykonywania (common language runtime — CLR).

Można również znaleźć w dokumentacji [STL/CLR](dotnet/stl-clr-library-reference.md) i [Biblioteka obsługi języka C++](dotnet/cpp-support-library.md).

## <a name="other-c-libraries"></a>Inne biblioteki języka C++

Ta sekcja zawiera łącza do bibliotek, które nie są uwzględniane w programie Visual Studio, ale można pobrać i używane z programem Visual C++.

[Zwiększanie wyniku](http://www.boost.org/)  
Biblioteka popularnych i powszechnie używane.

[C++ REST SDK](http://casablanca.codeplex.com).  
Biblioteka Microsoft do komunikowania się z usługami sieci web za pośrednictwem protokołu HTTP.

## <a name="more-resources"></a>Więcej zasobów

[Zasoby dla języka Visual C++](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
Więcej zasobów Visual C++.

[Standard C++](http://isocpp.org/)  
Dowiedz się o języku C++, uzyskaj omówienie nowoczesnego języka C++, znajdź łącza do książek, artykułów, rozmów i imprez

[Dowiedz się, Visual C++](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
Rozpocznij naukę języka C++.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C](c-language/c-language-reference.md)   
[Odwołanie do biblioteki wykonawcze języka C](c-runtime-library/c-run-time-library-reference.md)   
[Funkcje wewnętrzne kompilatora i język asemblera](intrinsics/compiler-intrinsics-and-assembly-language.md)
