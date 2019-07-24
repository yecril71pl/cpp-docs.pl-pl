---
title: Tworzenie C/C++ dll w Visual Studio
ms.date: 07/18/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 9f5b34fda8a429f8e55631e1e0125ed6f79d5bae
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341069"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Tworzenie C/C++ dll w Visual Studio

W systemie Windows biblioteka dołączana dynamicznie (DLL) to rodzaj pliku wykonywalnego, który działa jako udostępniona biblioteka funkcji i zasobów. Dynamiczne łączenie to możliwość systemu operacyjnego, która umożliwia plikowi wykonywalnemu wywoływanie funkcji lub korzystanie z zasobów przechowywanych w osobnym pliku. Te funkcje i zasoby można kompilować i wdrażać niezależnie od plików wykonywalnych, które z nich korzystają. Biblioteka DLL nie jest autonomicznym plikiem wykonywalnym; działa w kontekście aplikacji, która ją wywołuje. System operacyjny może załadować bibliotekę DLL do miejsca w pamięci aplikacji podczas ładowania aplikacji (niejawnego*łączenia*) lub na żądanie w czasie wykonywania (*jawne łączenie*). Biblioteki DLL ułatwiają także udostępnianie funkcji i zasobów w plikach wykonywalnych. Wiele aplikacji może jednocześnie uzyskać dostęp do zawartości pojedynczej kopii biblioteki DLL w pamięci.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Różnice między łączeniem dynamicznym i konsolidacją statyczną

Konsolidacja statyczna kopiuje wszystkie kody obiektów w bibliotece statycznej do plików wykonywalnych, które używają ich podczas kompilowania. Konsolidacja dynamiczna zawiera tylko te informacje, które są konieczne w systemie Windows w czasie wykonywania, aby zlokalizować i załadować bibliotekę DLL, która zawiera element danych lub funkcję. Podczas tworzenia biblioteki DLL należy również utworzyć bibliotekę importowaną, która zawiera te informacje. Podczas kompilowania pliku wykonywalnego, który wywołuje bibliotekę DLL, konsolidator używa eksportowanych symboli w bibliotece importu do przechowywania tych informacji dla modułu ładującego systemu Windows. Gdy moduł ładujący ładuje bibliotekę DLL, biblioteka DLL jest mapowana na przestrzeń pamięci aplikacji. Jeśli jest obecny, Funkcja specjalna w bibliotece DLL `DllMain`jest wywoływana w celu wykonania dowolnego inicjalizacji wymaganego przez bibliotekę DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Różnice między aplikacjami i bibliotekami DLL

Mimo że biblioteki DLL i aplikacje są modułami wykonywalnymi, różnią się one na kilka sposobów. Dla użytkownika końcowego najbardziej oczywistą różnicą jest to, że biblioteki DLL nie są aplikacjami, które mogą być wykonywane bezpośrednio. Z punktu widzenia systemu istnieją dwie podstawowe różnice między aplikacjami i bibliotekami DLL:

- Aplikacja może mieć jednocześnie uruchomione wiele wystąpień w systemie, natomiast biblioteka DLL może mieć tylko jedno wystąpienie.

- Aplikacja może zostać załadowana jako proces, który może mieć własne elementy, takie jak stos, wątki wykonywania, pamięć globalna, dojścia do plików i kolejka komunikatów, ale biblioteka DLL nie może.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Zalety korzystania z bibliotek DLL

Dynamiczne łączenie z kodem i zasobami zapewnia kilka korzyści w stosunku do konsolidacji statycznej:

- Konsolidacja dynamiczna oszczędza pamięć i zmniejsza wymianę. Wiele procesów może korzystać z biblioteki DLL jednocześnie, udostępniając jedną kopię części tylko do odczytu biblioteki DLL w pamięci. Natomiast każda aplikacja skompilowana przy użyciu biblioteki połączonej statycznie ma kompletną kopię kodu biblioteki, którą system Windows musi załadować do pamięci.

- Konsolidacja dynamiczna oszczędza miejsce na dysku i przepustowość. Wiele aplikacji może współużytkować jedną kopię biblioteki DLL na dysku. Natomiast każda aplikacja skompilowana przy użyciu biblioteki dołączanej statycznie ma kod biblioteki połączony z jego obrazem wykonywalnym, który zużywa więcej miejsca na dysku i wymaga większej przepustowości.

- Konserwacja, poprawki zabezpieczeń i uaktualnienia mogą być łatwiejsze. Gdy aplikacje korzystają z typowych funkcji w bibliotece DLL, tak długo, jak argumenty funkcji i wartości zwracane nie zmieniają się, można zaimplementować poprawki błędów i wdrożyć aktualizacje biblioteki DLL. Po zaktualizowaniu bibliotek DLL aplikacje, które ich używają, nie muszą zostać ponownie skompilowane ani połączone, a następnie używają nowej biblioteki DLL zaraz po jej wdrożeniu. W przeciwieństwie do tego, poprawki wprowadzane w statycznie połączonym kodzie obiektu muszą zostać ponownie połączone i wdrożone we wszystkich aplikacjach, które z nich korzystają.

- Aby zapewnić pomoc techniczną na rynku, można użyć bibliotek DLL. Na przykład biblioteka DLL sterownika wyświetlania może być modyfikowana w taki sposób, aby obsługiwała wyświetlanie, które nie były dostępne podczas wysyłania aplikacji.

- Za pomocą jawnego łączenia można odnajdywać i ładować biblioteki DLL w środowisku uruchomieniowym, takie jak rozszerzenia aplikacji, które dodają nowe funkcje do aplikacji bez konieczności ponownego kompilowania lub wdrażania.

- Konsolidacja dynamiczna ułatwia obsługę aplikacji pisanych w różnych językach programowania. Programy napisywane w różnych językach programowania mogą wywołać tę samą funkcję DLL, o ile programy przestrzegają konwencji wywoływania funkcji. Programy i funkcja DLL muszą być zgodne w następujący sposób: kolejność, w jakiej funkcja oczekuje, że jej argumenty mają być wypychane na stosie, niezależnie od tego, czy funkcja lub aplikacja jest odpowiedzialna za czyszczenie stosu, oraz czy wszystkie argumenty są Zakończono przekazywanie rejestrów.

- Dynamiczne łączenie zapewnia mechanizm rozszerzający klasy biblioteki MFC. Klasy można dziedziczyć z istniejących klas MFC i umieścić je w bibliotece DLL rozszerzenia MFC do użytku przez aplikacje MFC.

- Konsolidacja dynamiczna ułatwia tworzenie międzynarodowych wersji aplikacji. Biblioteki dll to wygodny sposób dostarczania zasobów specyficznych dla ustawień regionalnych, które znacznie ułatwiają tworzenie międzynarodowych wersji aplikacji. Zamiast dostarczania wielu zlokalizowanych wersji aplikacji, można umieścić ciągi i obrazy dla każdego języka w oddzielnej bibliotece DLL zasobów, a następnie aplikacja może załadować odpowiednie zasoby dla tych ustawień regionalnych w czasie wykonywania.

Potencjalną wadą korzystania z bibliotek DLL jest to, że aplikacja nie jest samodzielna. jest to zależne od istnienia oddzielnego modułu DLL, który należy wdrożyć lub zweryfikować jako część instalacji.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Więcej informacji na temat tworzenia i używania bibliotek DLL

Poniższe tematy zawierają szczegółowe informacje na temat tworzenia C/C++ dll w programie Visual Studio.

[Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
Zawiera opis sposobu tworzenia i używania biblioteki DLL przy użyciu Visual Studio.

[Rodzaje bibliotek DLL](kinds-of-dlls.md)<br/>
Dostarcza informacje dotyczące różnych rodzajów bibliotek DLL, które mogą być skompilowane.

[Biblioteka DLL — często zadawane pytania](dll-frequently-asked-questions.md)<br/>
Dostarcza odpowiedzi na często zadawane pytania dotyczące bibliotek DLL.

[Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md)<br/>
Opisuje jawne i niejawne łączenia z biblioteką DLL.

[Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
Omawia kod inicjujący DLL, który musi zostać wykonany w przypadku ładowania biblioteki DLL.

[Zachowanie biblioteki wykonawczej DLL i Visual C++](run-time-library-behavior.md)<br/>
Opisuje, jak biblioteka uruchomieniowa wykonuje sekwencję uruchamiania biblioteki DLL.

[LoadLibrary i AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
Omawia użycie  funkcji LoadLibrary `AfxLoadLibrary` i jawne łączenie z biblioteką DLL w czasie wykonywania.

[GetProcAddress](getprocaddress.md)<br/>
W tym artykule omówiono użycie polecenia **GetProcAddress** w celu uzyskania adresu eksportowanej funkcji w bibliotece DLL.

[FreeLibrary i AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
W tym  artykule omówiono `AfxFreeLibrary` użycie FreeLibrary i, gdy moduł dll nie jest już wymagany.

[Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
Zawiera opis ścieżki wyszukiwania używanej przez system operacyjny Windows do lokalizowania biblioteki DLL w systemie.

[Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
Opisuje Stany modułu zwykłej biblioteki MFC DLL dynamicznie połączonej z MFC.

[Biblioteki DLL rozszerzeń MFC](extension-dlls-overview.md)<br/>
Omawia biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku, pochodzące z istniejących klas biblioteki klas Microsoft Foundation.

[Tworzenie biblioteki DLL z samymi zasobami](creating-a-resource-only-dll.md)<br/>
Omawia bibliotekę zasobów DLL, która zawierają tylko zasoby, takie jak ikony, mapy bitowe, ciągi i okna dialogowe.

[Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
Oferuje rozszerzoną obsługę satelitarnej biblioteki DLL; jest to funkcja, która pomaga w tworzeniu aplikacji zlokalizowanej w wielu językach.

[Importowanie i eksportowanie](importing-and-exporting.md)<br/>
Zawiera opis importowania symboli publicznych do aplikacji lub eksportowania funkcji z biblioteki DLL

[Technologia Active i biblioteki DLL](active-technology-and-dlls.md)<br/>
Zezwala na implementowanie serwerów obiektów wewnątrz biblioteki DLL.

[Automatyzacja w bibliotece DLL](automation-in-a-dll.md)<br/>
Zawiera opis opcji automatyzacji w Kreatorze MFC DLL.

[Konwencje nazewnictwa bibliotek MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
Omawia ustrukturyzowaną konwencję nazewnictwa bibliotek DLL i bibliotek zawartych w MFC.

[Wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md)<br/>
Opisuje, jak wywoływać funkcje biblioteki DLL z aplikacji Visual Basic.

## <a name="related-sections"></a>Sekcje pokrewne

[Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
Opisuje regularne biblioteki DLL MFC, które umożliwiają korzystanie z biblioteki MFC jako części biblioteki dołączanej dynamicznie systemu Windows.

[Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)<br/>
Opisuje, jak można używać MFCxx. dll i MFCxxD. dll (gdzie x jest numerem wersji MFC) udostępnionych bibliotek dołączanych dynamicznie z aplikacjami MFC i bibliotekami DLL rozszerzenia MFC.
