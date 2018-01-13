---
title: Biblioteki dll w programie Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed3679d29b8d181e2cbd9896d0322fea634bfbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-in-visual-c"></a>Biblioteki DLL w programie Visual C++  
  
W systemie Windows biblioteki dołączanej (dynamicznie DLL) to rodzaj typu pliku wykonywalnego, który działa jako biblioteki udostępnionej, funkcje i zasobów. Konsolidacja dynamiczna jest funkcją systemu operacyjnego, które umożliwia plik wykonywalny do wywołania funkcji, lub Użyj zasobów przechowywanych w oddzielnym pliku. Te funkcje i zasoby można skompilować i wdrożyć osobno z plików wykonywalnych, które z nich korzystają. Biblioteki DLL nie jest autonomiczny plik wykonywalny; uruchamia go w kontekście aplikacji, która wywołuje go. System operacyjny można załadować biblioteki DLL do przestrzeni pamięci aplikacji, podczas ładowania aplikacji (*Konsolidacja niejawna*), lub na żądanie w czasie wykonywania (*Konsolidacja jawna*). Biblioteki DLL ułatwiają również udostępnianie funkcje i zasoby w plikach wykonywalnych. Wiele aplikacji można uzyskać dostępu do zawartości pojedynczej kopii biblioteki DLL w pamięci w tym samym czasie.  
  
## <a name="differences-between-dynamic-linking-and-static-linking"></a>Różnice między łączenie dynamicznej i statycznej konsolidacji  
  
Statyczne połączenie kopiuje cały kod obiektu w bibliotece statycznej do plików wykonywalnych, które należy użyć, jeśli zostały one utworzone. Konsolidacja dynamiczna zawiera tylko informacje wymagane przez system Windows w czasie wykonywania do lokalizowania i ładowania biblioteki DLL zawierającej element danych lub funkcji. Podczas tworzenia biblioteki DLL można również utworzyć biblioteki importu, który zawiera te informacje. Podczas tworzenia pliku wykonywalnego, który wywołuje biblioteki DLL konsolidator przechowuje symbole wyeksportowanej biblioteki importu te informacje dotyczące modułu ładującego systemu Windows. Podczas ładowania biblioteki DLL modułu ładującego plik DLL, który jest mapowany do obszaru pamięci aplikacji. Jeśli jest obecny, specjalnego funkcji w bibliotece DLL, `DllMain`, jest wywoływana w celu przeprowadzenia wszelkich inicjowania wymaga biblioteki DLL.  
  
<a name="differences-between-applications-and-dlls"></a>  
  
## <a name="differences-between-applications-and-dlls"></a>Różnice między aplikacjami a bibliotekami DLL  
  
Mimo że biblioteki dll i aplikacje są zarówno pliku wykonywalnego modułów, różnią się one na kilka sposobów. Dla użytkownika końcowego najbardziej oczywisty różnica polega na to, że biblioteki DLL nie są aplikacje, które mogą być wykonywane bezpośrednio. Z punktu widzenia systemu istnieją dwie podstawowe różnice między aplikacjami a bibliotekami DLL:  
  
-   Aplikacja może mieć wiele wystąpień się jednocześnie działa w systemie, biblioteki DLL mogą mieć tylko jedno wystąpienie.  
  
-   Aplikacji mogą być ładowane jako proces, który może posiadać rzeczy, takich jak stosu, wątki wykonywania, pamięci globalnej dojścia do plików i kolejki komunikatów, ale nie biblioteki DLL.  
  
<a name="advantages-of-using-dlls"></a>  
  
## <a name="advantages-of-using-dlls"></a>Zalety używania bibliotek DLL  
  
Konsolidacja dynamiczna zamiast statycznego łączenia kodu i zasobów oferuje wiele korzyści. Jeśli korzystasz z biblioteki dll, można zapisać miejsca w pamięci i zmniejszyć wymiany. Gdy wiele aplikacji można użyć pojedynczej kopii biblioteki DLL, można zaoszczędzić miejsce na dysku i pobrać przepustowości. Biblioteki dll może być wdrożony i zaktualizowane oddzielnie, które umożliwia dostarczanie aktualizacji pomocy technicznej i oprogramowania poza rynkowych bez konieczności odbudować i dostarczać cały kod. Biblioteki DLL są wygodny sposób umożliwiają określanie wartości ustawień regionalnych zasobów, które obsługuje programy obsługi wielu języków, a jej obsługi ułatwiają tworzenie międzynarodowej wersji aplikacji. Konsolidacja jawna można zezwolić aplikacji w taki sposób odnaleźć i załadować biblioteki dll w czasie wykonywania, takie jak rozszerzenia, które zapewniają nowe funkcje.  
  
Konsolidacja dynamiczna ma następujące zalety:  
  
-   Konsolidacja dynamiczna oszczędzić pamięć i zmniejsza wymiany. Wiele procesów służy biblioteki DLL równocześnie, udostępnianie pojedynczej kopii tylko do odczytu części biblioteki DLL w pamięci. Z kolei każda aplikacja, która została skompilowana przy użyciu biblioteki statycznie połączonej ma pełną kopię kod biblioteki systemu Windows musi być załadowana do pamięci.  
  
-   Konsolidacja dynamiczna zapisuje miejsca na dysku i przepustowości. Wiele aplikacji można udostępniać pojedynczej kopii DLL na dysku. Z kolei każda aplikacja utworzona przy użyciu biblioteki dołączanej statycznie ma kod biblioteki połączony obrazu wykonywalnego, który używa więcej miejsca na dysku i zajmuje więcej przepustowości do transferu.  
  
-   Konserwacji, poprawki zabezpieczeń i uaktualnienia mogą być łatwiejsze. Użycie aplikacji typowych funkcji w bibliotece DLL, następnie tak długo, jak argumenty funkcji i zwracanych wartościach nie należy zmieniać, można zaimplementować poprawki i wdrażanie aktualizacji do pliku DLL. Po zaktualizowaniu bibliotek DLL, aplikacje, które z nich korzystają nie muszą być ponownie kompilowane lub połączyć ponownie, a umożliwiają korzystanie z nowej biblioteki DLL, natychmiast po jej wdrożeniu. Z kolei poprawki wprowadzone w kodzie statycznie połączonego obiektu wymagane jest ponowne łączenie i wdrożenie każda aplikacja, która korzysta z niego.  
  
-   Aby zapewnić obsługę rynku wtórnym, można użyć bibliotek DLL. Na przykład sterownik ekranu DLL może być modyfikowany do obsługi wyświetlania, które nie były dostępne, gdy aplikacja został wysłany. Można użyć Konsolidacja jawna można załadować rozszerzenia aplikacji jako biblioteki dll i dodawanie nowych funkcji do aplikacji bez odbudowywania lub jego ponowne wdrożenie.  
  
-   Konsolidacja dynamiczna ułatwia obsługuje aplikacje napisane w różnych językach programowania. Programy napisane w różnych językach programowania można wywołać tej samej funkcji DLL, tak długo, jak programy wykonaj konwencja wywołania funkcji. Programy funkcji DLL musi być zgodna z w następujący sposób: kolejność, w której funkcja spodziewa się argumenty, aby zostać przeniesiony na stosie, czy funkcja lub aplikacja jest odpowiedzialny za wyczyszczenie stosu i czy są żadnych argumentów przekazywane w rejestrach.  
  
-   Konsolidacja dynamiczna zapewnia mechanizm rozszerzenia klasy biblioteki MFC. Można dziedziczyć klasy istniejących klas MFC i umieść je w bibliotekę DLL rozszerzenia MFC do użycia w aplikacjach MFC.  
  
-   Konsolidacja dynamiczna ułatwia tworzenie międzynarodowej wersji aplikacji. Zaznaczając zasoby specyficzne dla ustawień regionalnych w bibliotece DLL, jest znacznie ułatwia tworzenie międzynarodowej wersji aplikacji. Zamiast wysyłania wielu zlokalizowane wersje aplikacji, ciągi i obrazy dla każdego języka można umieścić w oddzielnych Biblioteka DLL zasobu, a następnie aplikacja może załadować odpowiednich zasobów dla ustawień regionalnych w czasie wykonywania.   
  
 Potencjalne wadą korzystania z biblioteki DLL jest aplikacja nie jest autonomiczną; To zależy od istnienia oddzielnego modułu biblioteki DLL, które należy wdrożyć lub dokonać weryfikacji w ramach instalacji.  
  
  
## <a name="more-information-on-how-to-create-and-use-dlls"></a>Więcej informacji na temat sposobu tworzenia i używania bibliotek DLL  
  
Poniższe tematy zawierają szczegółowe informacje o tym, jak do bibliotek DLL programu w języku Visual C++.  
  
 [Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 Zawiera opis sposobu tworzenia i używania biblioteki DLL przy użyciu Visual Studio.  
  
 [Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)  
 Dostarcza informacje dotyczące różnych rodzajów bibliotek DLL, które mogą być skompilowane.  
  
 [DLL — często zadawane pytania](../build/dll-frequently-asked-questions.md)  
 Dostarcza odpowiedzi na często zadawane pytania dotyczące bibliotek DLL.  
  
 [Łączenie pliku wykonywalnego z biblioteką DLL](../build/linking-an-executable-to-a-dll.md)  
 Opisuje jawne i niejawne łączenia z biblioteką DLL.  
  
 [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
 W tym artykule omówiono kod inicjowania biblioteki DLL, który musi być wykonywany podczas ładowania biblioteki DLL.  
  
 [Zachowanie biblioteki wykonawczej DLL i Visual C++](../build/run-time-library-behavior.md)  
 Opisuje, jak biblioteka uruchomieniowa wykonuje sekwencję uruchamiania biblioteki DLL.  
  
 [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 Omówienie korzystania z **LoadLibrary** i `AfxLoadLibrary` jawnie powiązać biblioteki DLL w czasie wykonywania.  
  
 [GetProcAddress](../build/getprocaddress.md)  
 Omówienie korzystania z **GetProcAddress** do uzyskiwania adresów wyeksportowanej funkcji w bibliotece DLL.  
  
 [FreeLibrary i AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 Omówienie korzystania z **FreeLibrary** i `AfxFreeLibrary` po modułu DLL nie jest już potrzebne.  
  
 [Ścieżka wyszukiwania używana przez system Windows do lokalizowania biblioteki DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 W tym artykule opisano ścieżki wyszukiwania, używaną do lokalizowania biblioteki DLL w systemie systemu operacyjnego Windows.  
  
 [Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 W tym artykule opisano Stany modułu regularne, które biblioteki MFC DLL połączone dynamicznie z MFC.  
  
 [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md)  
 Omawia biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku, pochodzące z istniejących klas biblioteki klas Microsoft Foundation.  
  
 [Tworzenie biblioteki DLL z samymi zasobami](../build/creating-a-resource-only-dll.md)  
 Omawia bibliotekę zasobów DLL, która zawierają tylko zasoby, takie jak ikony, mapy bitowe, ciągi i okna dialogowe.  
  
 [Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 Oferuje rozszerzoną obsługę satelitarnej biblioteki DLL; jest to funkcja, która pomaga w tworzeniu aplikacji zlokalizowanej w wielu językach.  
  
 [Importowanie i eksportowanie](../build/importing-and-exporting.md)  
 Zawiera opis importowania symboli publicznych do aplikacji lub eksportowania funkcji z biblioteki DLL  
  
 [Technologia Active i biblioteki DLL](../build/active-technology-and-dlls.md)  
 Umożliwia serwerom obiektu do zaimplementowania wewnątrz biblioteki DLL.  
  
 [Automatyzacja w bibliotece DLL](../build/automation-in-a-dll.md)  
 Zawiera opis opcji automatyzacji w Kreatorze MFC DLL.  
  
 [Konwencje nazewnictwa bibliotek MFC DLL](../build/naming-conventions-for-mfc-dlls.md)  
 Omawia ustrukturyzowaną konwencję nazewnictwa bibliotek DLL i bibliotek zawartych w MFC.  
  
 [Wywoływanie funkcji DLL z aplikacji języka Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)  
 Opisuje, jak wywoływać funkcje biblioteki DLL z aplikacji Visual Basic.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
 [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 W tym artykule opisano regularne biblioteki DLL MFC, które pozwalają na korzystanie z biblioteki MFC jako części biblioteki DLL systemu Windows.  
  
 [Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)  
 W tym artykule opisano, jak można użyć MFCxx.dll i MFCxxD.dll (gdzie x jest numerem wersji MFC) udostępnionych bibliotek DLL z aplikacji MFC i biblioteki DLL rozszerzeń MFC.  
