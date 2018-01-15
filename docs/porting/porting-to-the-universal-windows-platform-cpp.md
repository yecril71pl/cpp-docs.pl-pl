---
title: "Przenoszenie na platformę uniwersalną systemu Windows (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6dd42eae54f61d03d4d490a17cf1282e2d2e51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Przenoszenie na platformę uniwersalną systemu Windows (C++)
Informacje na temat portu istniejącego kodu C++ do platformy aplikacji systemu Windows 10, platformy uniwersalnej systemu Windows można znaleźć w tym temacie. Co oznacza termin *uniwersalnych* kodu mogą działać na dowolnym z urządzeń z systemem Windows 10, łącznie z pulpitu, telefonów, tabletów i przyszłości urządzenia z systemem Windows 10. Możesz utworzyć pojedynczego projektu i jeden interfejs użytkownika XAML base, który działa poprawnie na dowolnym urządzeniu z systemem Windows 10. Układ dynamiczny funkcji w języku XAML służy do zezwalania Interfejsie użytkownika aplikacji do dostosowania do rozmiarów ekranów.  
  
 Dokumentacja Centrum deweloperów systemu Windows zawiera przewodnik przy eksportowaniu Windows 8.1 aplikacji platformy uniwersalnej systemu Windows. Zobacz [przenoszenia ze środowiska wykonawczego systemu Windows 8 do platformy uniwersalnej systemu Windows](https://msdn.microsoft.com/windows/uwp/porting/w8x-to-uwp-root). Chociaż przewodnik koncentruje się przede wszystkim na kod w języku C#, większość porad ma zastosowanie do języka C++. Poniższe procedury zawierają więcej szczegółowych informacji.  
  
 Ten temat zawiera następujące procedury przenoszenia kodu platformy uniwersalnej systemu Windows.  
  
1.  [Eksportowanie aplikacji ze Sklepu Windows 8.1 do platformy uniwersalnej systemu Windows](#BK_81StoreApp)  
  
2.  [Eksportowanie składnika środowiska wykonawczego platformy uniwersalnej systemu Windows, Windows 8.1](#BK_81Component)  
  
 Jeśli masz klasycznego pulpitu DLL Win32 i chcesz wywołać go z aplikacji platformy uniwersalnej systemu Windows, możesz to zrobić również. Korzystanie z tych procedur, można utworzyć warstwę interfejsu użytkownika platformy uniwersalnej systemu Windows dla istniejącego pulpitu systemu Windows klasycznej aplikacji C++ lub standardowego kodu C++ i platform. Zobacz [porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
##  <a name="BK_81StoreApp"></a>Eksportowanie aplikacji ze Sklepu Windows 8.1 do platformy uniwersalnej systemu Windows  
 Jeśli masz aplikację ze Sklepu Windows 8.1 można Użyj tej procedury, aby przygotować go do pracy na platformy uniwersalnej systemu Windows i dowolne urządzenie z systemem Windows 10.  Jako projekt Windows 8.1, aby najpierw wyeliminować problemy, które wynikają z zmiany kompilatora i bibliotek jest dobrym pomysłem jest pierwszej kompilacji projektu z programu Visual Studio 2017 r. Po wykonaniu tego istnieją dwa sposoby Skonwertuj je do projektu platformy uniwersalnej systemu Windows do systemu Windows 10. Najprostszym sposobem (zgodnie z opisem w poniższej procedurze) jest utworzenie projektu uniwersalnej systemu Windows i skopiuj istniejący kod do niego. Jeśli uniwersalnych projektów były używane dla pulpitu Windows 8.1 i Windows 8.1 Phone, projekt zostanie uruchomiona z dwóch różnych układów w języku XAML, ale zakończenia z pojedynczy układ dynamiczne, które można dostosować do rozmiaru ekranu.  
  
#### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Do portu aplikacji Sklepu Windows 8.1, aby platformy uniwersalnej systemu Windows  
  
1.  Jeśli nie zostało to jeszcze zrobione, otwórz projekt aplikacji Windows 8.1 w programie Visual Studio 2017 r, a następnie postępuj zgodnie z instrukcjami, aby zaktualizować pliku projektu.  
  
     Musisz mieć zainstalowane narzędzia Windows 8.1 w Instalatorze programu Visual Studio. Jeśli nie masz te narzędzia są zainstalowane, uruchom Instalatora programu Visual Studio z okna programy i funkcje, Visual Studio 2017 lub w oknie Ustawienia wybrać **Modyfikuj**. Zlokalizuj narzędzia Windows 8.1, upewnij się, że jest zaznaczone i kliknij przycisk OK.  
  
2.  Otwórz okno właściwości projektu, a w języku C++ ogólne, ustaw zestaw narzędzi platformy v141, narzędzia kompilacji dla programu Visual Studio 2017 r.  
  
3.  Skompiluj projekt jako projekt Windows 8.1 i rozwiązać wszelkie błędy kompilacji. Błędy na tym etapie są prawdopodobnie ze względu na istotne zmiany w narzędzia kompilacji i bibliotek. Zobacz [Historia 2003 2015 zmian Visual C++](../porting/visual-cpp-change-history-2003-2015.md) szczegółowy opis zmian, które mogą mieć wpływ na kod.  
  
     Po projektu kompilacje prawidłowo, można przystąpić do portu na uniwersalnych systemu Windows (Windows 10).  
  
4.  Utwórz nowy projekt aplikacji uniwersalnej systemu Windows przy użyciu pustego szablonu. Możesz nadać jej takiej samej nazwie jak istniejącego projektu, mimo że w tym projektów musi być w różnych katalogach.  
  
5.  Zamknij rozwiązanie, a następnie za pomocą Eksploratora Windows lub wiersza polecenia, skopiuj pliki kodu (z rozszerzenia .cpp, .h i .xaml) z projektu Windows 8.1 w tym samym folderze co plik projektu (.vcxproj) dla projektu, który został utworzony w kroku 1. Wykonaj skopiuj plik Package.appxmanifest, a jeśli masz oddzielny kod pulpitu Windows 8.1 i telefonu, wybierz jeden z nich do portu pierwszej (będziesz mieć wykonania dodatkowych czynności później w celu dostosowania do innych). Pamiętaj, aby kopiowania, podfoldery i ich zawartość. Jeśli zostanie wyświetlony monit, należy wybrać opcję Zastąp wszystkie pliki o takich samych nazwach.  
  
6.  Otwórz rozwiązanie, a następnie wybierz pozycję **Dodaj, istniejący element** z menu skrótów węzła projektu. Wybierz pliki, które zostały skopiowane, z wyjątkiem przypadków, które są już częścią projektu.  
  
     Sprawdź wszystkie podfoldery i upewnij się dodać pliki do nich również.  
  
7.  Jeśli nie używasz z tej samej nazwy projektu jako starego projektu, otwórz plik Package.appxmanifest i zaktualizować punkt wejścia w celu odzwierciedlenia nazwy przestrzeni nazw dla klasy aplikacji.  
  
     **Punktu wejścia** polem w pliku Package.appxmanifest zawiera nazwę zakresie klasy aplikacji, która zawiera obszar nazw zawiera klasy aplikacji. Podczas tworzenia projektu uniwersalnej systemu Windows, przestrzeń nazw ma ustawioną nazwę projektu. Jeśli jest inny niż nowości w plikach skopiowane z projektu stare, należy zaktualizować jednego lub drugiego, aby były zgodne.  
  
8.  Skompiluj projekt i rozwiązać wszelkie błędy kompilacji, ze względu na istotne zmiany między różnymi wersjami zestawu Windows SDK.  
  
9. Uruchom projekt na komputerze lokalnym. Sprawdź, czy nie ma żadnych błędów wdrożenia i że układ aplikacji wygląda uzasadnione i że działa ona prawidłowo na pulpicie.  
  
10. Jeśli masz kod oddzielnych plików i .xaml na inne urządzenie, takie jak Windows Phone 8.1, Sprawdź ten kod i zidentyfikować, gdzie różni się od standardowego urządzenia. Różnica polega tylko układ, można użyć Visual State Manager w kodzie xaml, aby dostosować wyświetlanie zależnie od wielkości ekranu. Inne różnice można użyć warunków sekcje w kodzie za pomocą następujących instrukcji #if.  
  
    ```  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
    ```  
  
     Te instrukcje odpowiednio mają zastosowanie do aplikacji ze Sklepu Windows, Sklep Windows Phone aplikacje, zarówno lub żadna (klasycznej Win32 tylko wersja desktop). Makra te są dostępne tylko w systemie Windows 8.1 SDK i nowszych, jeśli kod wymaga kompilacji z wcześniejszych wersji zestawu Windows SDK lub dla innych platform, oprócz systemu Windows, należy również rozważyć przypadku że żaden z nich, a następnie są zdefiniowane.  
  
11. Uruchom i debugowanie aplikacji na emulator lub urządzenie fizyczne, dla każdego typu urządzenia, które obsługuje aplikację. Aby uruchomić emulatora, musisz uruchomić program Visual Studio na komputerze fizycznym, a nie maszyny wirtualnej.  
  
##  <a name="BK_81Component"></a>Eksportowanie składnika środowiska wykonawczego platformy uniwersalnej systemu Windows, Windows 8.1  
 Jeśli masz biblioteki DLL lub składnika środowiska uruchomieniowego systemu Windows, który już działa z aplikacji ze Sklepu Windows 8.1 można Użyj tej procedury, można pobrać składnika lub DLL, Praca z platformy uniwersalnej systemu Windows i Windows 10. Podstawowa procedura polega na utworzenie nowego projektu i skopiuj do niego kodu.  
  
#### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Port składnika środowiska uruchomieniowego Windows 8.1, platformy uniwersalnej systemu Windows  
  
1.  W **nowy projekt** okna dialogowego w programie Visual Studio 2017 r, Znajdź **uniwersalnych systemu Windows** węzła. Jeśli nie widzisz ten węzeł, zainstaluj [narzędzi dla systemu Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903) pierwszy. Wybierz **składnika środowiska wykonawczego systemu Windows** szablonu, nadaj nazwę dla składnika, a następnie wybierz pozycję **OK** przycisku. Nazwa składnika będzie służyć jako nazwy przestrzeni nazw, należy użyć takiej samej nazwie jak swoje projekty stary obszar nazw. Wymaga to utworzyć projekt w innym folderze od starego. Jeśli wybierzesz inną nazwę, należy zaktualizować nazwę przestrzeni nazw w plikach wygenerowanego kodu.  
  
2.  Zamknij projekt.  
  
3.  Skopiuj wszystkie pliki kodu (.cpp, .h, .xaml itp.) z składnika Windows 8.1 do nowo utworzonego projektu. Nie Kopiuj pliku Package.appxmanifest.  
  
4.  Skompiluj i usuń wszelkie błędy ze względu na istotne zmiany między różnymi wersjami zestawu Windows SDK.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Mogą wystąpić różne błędy w trakcie procesu Eksportowanie kodu dla platformy uniwersalnej systemu Windows. Poniżej przedstawiono niektóre możliwe problemy, które mogą wystąpić.  
  
 **Problemy z konfiguracją projektu**  
  
 Zgłoszony błąd:  
  
```Output  
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable  
```  
  
 W takim przypadku nie tworzy projekt jako projekt uniwersalnych systemu Windows. Sprawdź plik projektu i upewnij się, że ma prawidłowe elementów XML, określających projektu jako uniwersalnych projektów systemu Windows. Następujące elementy powinien znajdować się (numer wersji platformy docelowej mogą się różnić):  
  
```xml  
<AppContainerApplication>true</AppContainerApplication>  
<ApplicationType>Windows Store</ApplicationType>  
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
```  
  
 Jeśli utworzono nowy projekt platformy uniwersalnej systemu Windows przy użyciu programu Visual Studio, nie powinno być widoczne tego błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik przenoszenia Visual C++](../porting/porting-to-the-universal-windows-platform-cpp.md)   
 [Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)
