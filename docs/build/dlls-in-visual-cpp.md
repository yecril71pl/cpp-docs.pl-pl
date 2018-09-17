---
title: Biblioteki dll w programie Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28be2caa3477eabc8b717b387c99d65585a9ef19
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718058"
---
# <a name="dlls-in-visual-c"></a>Biblioteki DLL w programie Visual C++

W Windows biblioteki dołączanej (dynamicznie DLL) jest rodzaj pliku wykonywalnego, który działa jako współdzielona biblioteka funkcji i zasobów. Konsolidacja dynamiczna jest funkcją systemu operacyjnego, która umożliwia plik wykonywalny do wywołania funkcji lub korzystać z zasobów przechowywanych w oddzielnym pliku. Te funkcje i zasoby można skompilowana i wdrożona oddzielnie od plików wykonywalnych, które z nich korzystają. Biblioteka DLL nie jest autonomicznym plikiem wykonywalnym; działa w kontekście aplikacji, który ją wywołuje. System operacyjny może załadować biblioteki DLL do przestrzeni pamięci aplikacji po załadowaniu aplikacji (*niejawna Konsolidacja*), lub na żądanie w czasie wykonywania (*jawne tworzenie łączy*). Biblioteki DLL ułatwiają również udostępniać funkcje i zasoby w plikach wykonywalnych. Wiele aplikacji można uzyskać dostęp do zawartości pojedynczej kopii biblioteki DLL w pamięci, w tym samym czasie.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Różnice między dynamiczne łączenie i łączenie statyczne

Łączenie statyczne kopiuje całego kodu obiektowego w bibliotece statycznej do plików wykonywalnych, które należy użyć, jeśli zostały one utworzone. Konsolidacja dynamiczna zawiera tylko informacje wymagane przez Windows w czasie wykonywania do lokalizowania i ładowania biblioteki DLL, który zawiera element danych lub funkcji. Podczas tworzenia biblioteki DLL, możesz również utworzyć bibliotekę importu, który zawiera te informacje. Podczas tworzenia pliku wykonywalnego, który wywołuje bibliotekę DLL, konsolidator używa wyeksportowanego symboli w bibliotece importu do przechowywania tych informacji do modułu ładującego Windows. Podczas ładowania biblioteki DLL modułu ładującego biblioteki DLL jest zamapowana na obszar pamięci aplikacji. Jeśli jest obecny, specjalnej funkcji w bibliotece DLL, `DllMain`, jest wywoływana w celu przeprowadzenia wszelkich inicjowania biblioteki DLL wymaga.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Różnice między aplikacjami a bibliotekami DLL

Mimo że biblioteki dll i aplikacje są zarówno pliku wykonywalnego modułów, różnią się one na kilka sposobów. Dla użytkownika końcowego najbardziej oczywiste różnica polega na to, że biblioteki DLL nie są aplikacje, które mogą być wykonywane bezpośrednio. Z punktu widzenia systemu istnieją dwie podstawowe różnice między aplikacjami a bibliotekami DLL:

- Aplikacja może mieć wielu wystąpień sam jednocześnie działa w systemie, biblioteki DLL mogą mieć tylko jedno wystąpienie.

- Aplikacja może być załadowany jako proces, który może mieć elementy, takie jak stos, wątki wykonywania, globalnej pamięci, dojścia do plików i kolejki komunikatów, ale nie biblioteki DLL.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Zalety używania bibliotek DLL

Łączenia dynamicznego zamiast statycznego do kodu i zasobów ma kilka zalet. Gdy używasz biblioteki dll, można zaoszczędzić miejsce w pamięci i zmniejszają. Gdy wiele aplikacji, można użyć pojedynczej kopii biblioteki DLL, można zaoszczędzić miejsce na dysku i pobrać przepustowości. Biblioteki dll mogą być wdrażane i aktualizowane oddzielnie, pozwalającej zapewnienia pomocy technicznej oraz aktualizowanie oprogramowania posprzedażne bez konieczności ponownego kompilowania i dostarczaj całego kodu. Biblioteki DLL są wygodny sposób dostarczania zasobów specyficznych dla ustawień regionalnych, które obsługują wiele języków programy, a jej obsługi ułatwiają tworzenie międzynarodowych wersji aplikacji. Jawne tworzenie łączy, można zezwolić aplikacji wykrycie i załadowanie biblioteki dll w czasie wykonywania, takie jak rozszerzenia, które udostępniają nowe możliwości.

Konsolidacja dynamiczna ma następujące zalety:

- Konsolidacja dynamiczna zużycie pamięci i zmniejsza zamianę. Wiele procesów służy biblioteki DLL jednocześnie udostępnianie jednej kopii tylko do odczytu części biblioteki DLL w pamięci. Z kolei każda aplikacja, która powstała przy użyciu statycznie połączone biblioteki ma pełną kopię kodu biblioteki, który Windows należy załadować do pamięci.

- Konsolidacja dynamiczna zapisuje miejsca na dysku i przepustowości. Wiele aplikacji można udostępniać pojedynczej kopii biblioteki DLL na dysku. Z kolei każda aplikacja utworzona za pomocą biblioteki dołączanej zawiera kod biblioteki podłączonymi do jego obrazu pliku wykonywalnego, który używa więcej miejsca na dysku i Trwa większej przepustowości do transferu.

- Poprawki zabezpieczeń, konserwacja i uaktualnienia mogą stanowić łatwiejsze. Użycie aplikacji typowych funkcji w bibliotece DLL, następnie tak długo, jak nie zmieniaj argumenty funkcji i zwracanych wartości, można zaimplementować poprawki błędów i wdrażać aktualizacje do biblioteki DLL. Po zaktualizowaniu bibliotek DLL, aplikacji, które z nich korzystają nie muszą być ponownie kompilowane lub połączyć ponownie, a oni skorzystać z nowej biblioteki DLL zaraz po jego wdrożeniu. W odróżnieniu od nich poprawek, które wprowadzasz w kodzie statycznie połączonego obiektu wymagają Połącz ponownie i Wdróż ponownie każdą aplikacją, która korzysta z niego.

- Aby umożliwiają wsparcie posprzedażne, można użyć bibliotek DLL. Na przykład można zmodyfikować sterownik ekranu biblioteki DLL do obsługi wyświetlania, które nie były dostępne, gdy aplikacja zostało wysłane. Ładowanie rozszerzenia aplikacji jako biblioteki DLL za pomocą jawnego łączenia i dodawania nowych funkcji do aplikacji bez przebudowa lub jej ponownego wdrażania.

- Konsolidacja dynamiczna ułatwia obsługuje aplikacje napisane w różnych językach programowania. Programy napisane w różnych językach programowania, można wywołać tej samej funkcji DLL, tak długo, jak programy postępuj zgodnie z Konwencją wywoływania funkcji. Programy i funkcji DLL musi być zgodny w następujący sposób: kolejność, w której funkcja oczekuje argumentów ma zostać wypchnięty na stos, czy funkcja lub aplikacja jest odpowiedzialny za Oczyszczanie stosu i czy są argumenty przekazywane w rejestrach.

- Dynamiczne łączenie umożliwia mechanizm rozszerzenia klas bibliotek MFC. Można dziedziczyć klasy z istniejących klas MFC i umieszczenie ich w rozszerzenia MFC biblioteki DLL do użytku przez aplikacje MFC.

- Konsolidacja dynamiczna ułatwia tworzenie międzynarodowych wersji aplikacji. Wprowadzenie do ustawień regionalnych specyficznych dla zasobów w bibliotece DLL, jest znacznie ułatwiają tworzenie międzynarodowych wersji aplikacji. Zamiast wysyłania wielu zlokalizowane wersje aplikacji, można umieścić ciągów i obrazów dla każdego z języków, które znajdują się w oddzielnych Biblioteka DLL zasobu, a następnie aplikacja mogła ładować odpowiednie zasoby dla danego ustawienia regionalnego w czasie wykonywania.

Potencjalne wadą korzystania z biblioteki DLL jest aplikacja nie jest niezależna; To zależy od istnienia oddzielny moduł DLL, który należy wdrożyć lub dokonać weryfikacji w ramach instalacji.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Więcej informacji na temat tworzenia i używania biblioteki dll

Poniższe tematy zawierają szczegółowe informacje o tym, jak program bibliotek DLL w programie Visual C++.

[Wskazówki: Tworzenie i używanie biblioteki łączy dynamicznych (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md) w tym artykule opisano sposób tworzenia i używania biblioteki DLL przy użyciu programu Visual Studio.

[Rodzaje bibliotek DLL](../build/kinds-of-dlls.md) informacje na temat różnych rodzajów bibliotek DLL, które mogą być tworzone.

[DLL — często zadawane pytania](../build/dll-frequently-asked-questions.md) zawiera odpowiedzi na często zadawane pytania dotyczące bibliotek DLL.

[Łączenie pliku wykonywalnego z biblioteką DLL](../build/linking-an-executable-to-a-dll.md) opisuje jawne i niejawne łączenia z biblioteką DLL.

[Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll) omawia kod inicjalizacji biblioteki DLL, która musi być wykonany kiedy DLL się ładuje.

[Biblioteki dll i zachowanie biblioteki wykonawczej języka Visual C++](../build/run-time-library-behavior.md) w tym artykule opisano, jak biblioteki wykonawczej wykonuje sekwencję uruchamiania biblioteki DLL.

[LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) omawia przy użyciu **LoadLibrary** i `AfxLoadLibrary` jawne łącze do biblioteki DLL w czasie wykonywania.

[GetProcAddress](../build/getprocaddress.md) omawia przy użyciu **GetProcAddress** celu uzyskania adresu eksportowanych funkcji w bibliotece DLL.

[FreeLibrary i AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md) omawia przy użyciu **FreeLibrary** i `AfxFreeLibrary` gdy moduł DLL nie jest już potrzebny.

[Kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order) opisuje ścieżkę wyszukiwania, używany przez system operacyjny Windows do lokalizowania biblioteki DLL w systemie.

[Stany modułu regularne biblioteki MFC DLL połączone dynamicznie z MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md) opisuje Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC.

[Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md) wyjaśnia dll, które zazwyczaj implementują klasy wielokrotnego użytku pochodzące z istniejących klas biblioteki klas Microsoft Foundation.

[Tworzenie biblioteki DLL Resource-Only](../build/creating-a-resource-only-dll.md) w tym artykule omówiono tylko zasobów DLL, która zawiera zasoby, takie jak ikony, mapy bitowe, ciągi i okna dialogowe.

[Zasoby zlokalizowane w aplikacjach MFC: satelitarne biblioteki dll](../build/localized-resources-in-mfc-applications-satellite-dlls.md) oferuje rozszerzoną obsługę satelitarnej biblioteki dll, funkcja, która pomaga w tworzeniu aplikacji zlokalizowanej w wielu językach.

[Importowanie i eksportowanie](../build/importing-and-exporting.md) zawiera opis importowania symboli publicznych do aplikacji lub eksportowania funkcji z biblioteki DLL

[Biblioteki dll i technologii Active](../build/active-technology-and-dlls.md) umożliwia serwerom obiektu do zaimplementowania wewnątrz biblioteki DLL.

[Automatyzacja w bibliotece DLL](../build/automation-in-a-dll.md) w tym artykule opisano, co dostarcza opcji automatyzacji w Kreatorze MFC DLL.

[Konwencje nazewnictwa bibliotek MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions) w tym artykule omówiono, jak wykonać ustrukturyzowaną konwencję nazewnictwa bibliotek DLL i bibliotek zawartych w MFC.

[Wywoływanie funkcji DLL z aplikacji języka Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md) opisano, jak wywoływać funkcje biblioteki DLL z aplikacji Visual Basic.

## <a name="related-sections"></a>Sekcje pokrewne

[Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md) opisuje regularne biblioteki DLL MFC, które umożliwiają korzystanie z biblioteki MFC jako części biblioteki dll Windows.

[Biblioteka DLL wersji biblioteki MFC](../mfc/tn033-dll-version-of-mfc.md) opisano, jak można użyć MFCxx.dll i MFCxxD.dll (gdzie x jest numerem wersji MFC) udostępnionych bibliotek DLL z aplikacji MFC i biblioteki DLL rozszerzeń MFC.
