---
title: Tworzenie C/C++ dll w Visual Studio
description: Omówienie przyczyn i sposobu tworzenia bibliotek DLL i używania ich C++ w programie Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821424"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Tworzenie C/C++ dll w Visual Studio

W systemie Windows biblioteka dołączana dynamicznie (DLL) to rodzaj pliku wykonywalnego, który działa jako udostępniona biblioteka funkcji i zasobów. Dynamiczne łączenie to możliwość systemu operacyjnego. Umożliwia plikowi wykonywalnemu wywoływanie funkcji lub użycie zasobów przechowywanych w osobnym pliku. Te funkcje i zasoby można kompilować i wdrażać niezależnie od plików wykonywalnych, które z nich korzystają.

Biblioteka DLL nie jest autonomicznym plikiem wykonywalnym. Biblioteki DLL działają w kontekście aplikacji, które je wywołują. System operacyjny ładuje bibliotekę DLL do przestrzeni pamięci aplikacji. Jest to możliwe, gdy aplikacja jest ładowana (*niejawne konsolidacja*) lub na żądanie w czasie wykonywania (*jawne łączenie*). Biblioteki DLL ułatwiają także udostępnianie funkcji i zasobów w plikach wykonywalnych. Wiele aplikacji może jednocześnie uzyskać dostęp do zawartości pojedynczej kopii biblioteki DLL w pamięci.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Różnice między łączeniem dynamicznym i konsolidacją statyczną

Konsolidacja statyczna kopiuje wszystkie kody obiektów w bibliotece statycznej do plików wykonywalnych, które używają ich podczas kompilowania. Konsolidacja dynamiczna zawiera tylko te informacje, które są konieczne w systemie Windows w czasie wykonywania, aby zlokalizować i załadować bibliotekę DLL, która zawiera element danych lub funkcję. Podczas tworzenia biblioteki DLL należy również utworzyć bibliotekę importowaną, która zawiera te informacje. Podczas kompilowania pliku wykonywalnego, który wywołuje bibliotekę DLL, konsolidator używa eksportowanych symboli w bibliotece importu do przechowywania tych informacji dla modułu ładującego systemu Windows. Gdy moduł ładujący ładuje bibliotekę DLL, biblioteka DLL jest mapowana na przestrzeń pamięci aplikacji. Jeśli jest obecny, Funkcja specjalna w bibliotece DLL, `DllMain`, jest wywoływana w celu wykonania dowolnego inicjalizacji wymaganego przez bibliotekę DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Różnice między aplikacjami i bibliotekami DLL

Mimo że biblioteki DLL i aplikacje są modułami wykonywalnymi, różnią się one na kilka sposobów. Najbardziej oczywistą różnicą jest to, że nie można uruchomić biblioteki DLL. Z punktu widzenia systemu istnieją dwie podstawowe różnice między aplikacjami i bibliotekami DLL:

- Aplikacja może mieć jednocześnie uruchomione wiele wystąpień w systemie. Biblioteka DLL może mieć tylko jedno wystąpienie.

- Aplikacja może zostać załadowana jako proces. Mogą to być elementy, takie jak stos, wątki wykonywania, pamięć globalna, dojścia do plików i kolejka komunikatów. Biblioteka DLL nie może być własnością tych elementów.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Zalety korzystania z bibliotek DLL

Dynamiczne łączenie z kodem i zasobami zapewnia kilka korzyści w stosunku do konsolidacji statycznej:

- Konsolidacja dynamiczna oszczędza pamięć i zmniejsza wymianę. Wiele procesów może korzystać z biblioteki DLL jednocześnie, udostępniając jedną kopię części tylko do odczytu biblioteki DLL w pamięci. Natomiast każda aplikacja skompilowana przy użyciu biblioteki połączonej statycznie ma kompletną kopię kodu biblioteki, którą system Windows musi załadować do pamięci.

- Konsolidacja dynamiczna oszczędza miejsce na dysku i przepustowość. Wiele aplikacji może współużytkować jedną kopię biblioteki DLL na dysku. Natomiast każda aplikacja skompilowana przy użyciu biblioteki dołączanej statycznie ma kod biblioteki połączony w jego obraz wykonywalny. Spowoduje to użycie większej ilości miejsca na dysku i wymaga przetransferowania większej przepustowości.

- Ułatwienia konserwacji, poprawki zabezpieczeń i uaktualnienia mogą być łatwiejsze. Gdy aplikacje korzystają z typowych funkcji w bibliotece DLL, można zaimplementować poprawki błędów i wdrażać aktualizacje do biblioteki DLL. Po zaktualizowaniu bibliotek DLL nie trzeba ponownie kompilować ani łączyć aplikacji, które z nich korzystają. Mogą oni korzystać z nowej biblioteki DLL zaraz po jej wdrożeniu. Natomiast w przypadku wprowadzania poprawek w statycznie połączonym kodzie obiektu należy ponownie połączyć i wdrożyć wszystkie aplikacje, które z nich korzystają.

- Aby zapewnić pomoc techniczną na rynku, można użyć bibliotek DLL. Na przykład biblioteka DLL sterownika wyświetlania może być modyfikowana w taki sposób, aby obsługiwała wyświetlanie, które nie były dostępne podczas wysyłania aplikacji.

- Za pomocą jawnego łączenia można odnajdywać i ładować biblioteki DLL w czasie wykonywania. Na przykład rozszerzenia aplikacji, które dodają nowe funkcje do aplikacji bez konieczności jej odbudowywania lub ponownego wdrożenia.

- Konsolidacja dynamiczna ułatwia obsługę aplikacji pisanych w różnych językach programowania. Programy napisywane w różnych językach programowania mogą wywołać tę samą funkcję DLL, o ile programy przestrzegają konwencji wywoływania funkcji. Programy i funkcja DLL muszą być zgodne w następujący sposób: kolejność, w jakiej funkcja oczekuje, że jej argumenty mają być wypychane na stosie. Określa, czy funkcja lub aplikacja jest odpowiedzialna za czyszczenie stosu. I, czy wszystkie argumenty są przekazane do rejestrów.

- Dynamiczne łączenie zapewnia mechanizm rozszerzający klasy Microsoft Foundation Class Library (MFC). Klasy można dziedziczyć z istniejących klas MFC i umieścić je w bibliotece DLL rozszerzenia MFC do użytku przez aplikacje MFC.

- Konsolidacja dynamiczna ułatwia tworzenie międzynarodowych wersji aplikacji. Biblioteki dll to wygodny sposób dostarczania zasobów specyficznych dla ustawień regionalnych, które znacznie ułatwiają tworzenie międzynarodowych wersji aplikacji. Zamiast wysyłania wielu zlokalizowanych wersji aplikacji, można umieścić ciągi i obrazy dla każdego języka w oddzielnej bibliotece DLL zasobów. Następnie aplikacja może załadować odpowiednie zasoby dla tych ustawień regionalnych w czasie wykonywania.

Potencjalną wadą korzystania z bibliotek DLL jest to, że aplikacja nie jest samodzielna. Jest to zależne od istnienia oddzielnego modułu DLL: takiego, który należy wdrożyć lub zweryfikować jako część instalacji.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Więcej informacji na temat tworzenia i używania bibliotek DLL

Poniższe artykuły zawierają szczegółowe informacje na temat sposobu tworzenia C/C++ dll w programie Visual Studio.

[Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznieC++()](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Zawiera opis sposobu tworzenia i używania biblioteki DLL przy użyciu Visual Studio.

[Rodzaje bibliotek dll](kinds-of-dlls.md)\
Dostarcza informacje dotyczące różnych rodzajów bibliotek DLL, które mogą być skompilowane.

[Biblioteka DLL — często zadawane pytania](dll-frequently-asked-questions.md)\
Dostarcza odpowiedzi na często zadawane pytania dotyczące bibliotek DLL.

[Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md)\
Opisuje jawne i niejawne łączenia z biblioteką DLL.

[Inicjowanie\ dll](run-time-library-behavior.md#initializing-a-dll)
Omawia kod inicjujący DLL, który musi zostać wykonany w przypadku ładowania biblioteki DLL.

Biblioteki [dll i C++ zachowanie biblioteki w czasie wykonywania wizualizacji](run-time-library-behavior.md)\
Opisuje sekwencję uruchamiania biblioteki DLL w czasie wykonywania.

Funkcja [LoadLibrary i AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
W tym artykule omówiono używanie `LoadLibrary` i `AfxLoadLibrary` do jawnego łączenia z biblioteką DLL w czasie wykonywania.

\ [GetProcAddress](getprocaddress.md)
W tym artykule omówiono użycie `GetProcAddress` do uzyskania adresu eksportowanej funkcji w bibliotece DLL.

[FreeLibrary i AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
W tym artykule omówiono używanie `FreeLibrary` i `AfxFreeLibrary`, gdy moduł DLL nie jest już wymagany.

[Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)\
Zawiera opis ścieżki wyszukiwania używanej przez system operacyjny Windows do lokalizowania biblioteki DLL w systemie.

[Stany modułu zwykłej biblioteki MFC DLL dynamicznie połączonej z MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
Opisuje Stany modułu zwykłej biblioteki MFC DLL dynamicznie połączonej z MFC.

[Biblioteki DLL rozszerzenia MFC](extension-dlls-overview.md)\
Objaśnia biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku, pochodzące z istniejących klas MFC.

[Tworzenie\ dll tylko dla zasobów](creating-a-resource-only-dll.md)
Omawia bibliotekę zasobów DLL, która zawierają tylko zasoby, takie jak ikony, mapy bitowe, ciągi i okna dialogowe.

[Zlokalizowane zasoby w aplikacjach MFC: satelitarne biblioteki dll](localized-resources-in-mfc-applications-satellite-dlls.md)\
Oferuje rozszerzoną obsługę satelitarnej biblioteki DLL; jest to funkcja, która pomaga w tworzeniu aplikacji zlokalizowanej w wielu językach.

[Importowanie i eksportowanie](importing-and-exporting.md)\
Zawiera opis importowania symboli publicznych do aplikacji lub eksportowania funkcji z biblioteki DLL

[Aktywna technologia i biblioteki dll](active-technology-and-dlls.md)\
Zezwala na implementowanie serwerów obiektów wewnątrz biblioteki DLL.

[Automatyzacja w bibliotece DLL](automation-in-a-dll.md)\
Zawiera opis opcji automatyzacji w Kreatorze MFC DLL.

[Konwencje nazewnictwa dla bibliotek DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Omawia ustrukturyzowaną konwencję nazewnictwa bibliotek DLL i bibliotek zawartych w MFC.

[Wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md)\
Opisuje, jak wywoływać funkcje biblioteki DLL z aplikacji Visual Basic.

## <a name="related-sections"></a>Sekcje pokrewne

[Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
Opisuje regularne biblioteki DLL MFC, które umożliwiają korzystanie z biblioteki MFC jako części biblioteki dołączanej dynamicznie systemu Windows.

[Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)\
Opisuje, jak można używać MFCxx. dll i MFCxxD. dll (gdzie x jest numerem wersji MFC) udostępnionych bibliotek dołączanych dynamicznie z aplikacjami MFC i bibliotekami DLL rozszerzenia MFC.
