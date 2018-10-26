---
title: Przenoszenie na platformę Windows Universal (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16fe66e6ba8ea3f6e4f88f434b58c61d46ce1edb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080653"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Przenoszenie na platformę uniwersalną systemu Windows (C++)

W tym temacie można znaleźć informacji o sposobie przeniesiesz istniejący kod C++, platformy aplikacji systemu Windows 10, platformy uniwersalnej Windows. Co oznacza termin *universal* jest, że Twój kod może działać na dowolnym urządzeniu z systemem Windows 10, łącznie z pulpitu, telefonów, tabletów i przyszłych urządzeń z systemem Windows 10. Możesz utworzyć pojedynczy interfejs użytkownika XAML podstawowy, który działa również na dowolnym urządzeniu z systemem Windows 10 i jednego projektu. Aby zezwolić na Interfejsie użytkownika aplikacji dostosować je do rozmiarów ekranów, można użyć funkcji układ dynamiczny w XAML.

Dokumentację z Centrum deweloperów Windows zawiera przewodnik przenoszenia aplikacji Windows 8.1 do uniwersalnej platformy Windows. Zobacz [przenieść z środowiska uruchomieniowego Windows 8 do platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root). Chociaż przewodnik koncentruje się głównie na kod w języku C#, większość porad ma zastosowanie do języka C++. Poniższe procedury zawierają więcej szczegółowych informacji.

Ten temat zawiera poniższe procedury, aby przenoszenie kodu do platformy uniwersalnej systemu Windows.

- [Przenoszenie aplikacji App Store Windows 8.1 do platformy uniwersalnej systemu Windows](#BK_81StoreApp)

- [Przenoszenie składnika wykonawczego Windows 8.1 do platformy uniwersalnej systemu Windows](#BK_81Component)

Jeśli masz klasycznego pulpitu Win32 plik DLL, i chcesz wywołać go z aplikacją platformy uniwersalnej systemu Windows, możesz zrobić to w także. Korzystanie z tych procedur, można utworzyć warstwę interfejsu użytkownika platformy uniwersalnej systemu Windows, dla istniejącego pulpitu Windows klasycznych aplikacji języka C++ lub standardowego kodu C++ dla wielu platform. Zobacz [porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

## <a name="BK_81StoreApp"></a> Przenoszenie aplikacji App Store Windows 8.1 do platformy uniwersalnej systemu Windows

W przypadku aplikacji systemu Windows 8.1 Store służy tej procedury, aby przygotować go do pracy na platformy uniwersalnej systemu Windows i na dowolnym urządzeniu z systemem Windows 10.  Jako projekt Windows 8.1, najpierw wyeliminowanie wszelkich problemów, które wynikają z zmiany w kompilatorze i bibliotekach jest dobry pomysł, aby pierwsza kompilacja projektu programu Visual Studio 2017. Po jego wykonaniu istnieją dwa sposoby skonwertuje ją do projektu UWP systemu Windows 10. Najłatwiejszy sposób (jak wyjaśniono w poniższej procedurze) jest utworzenie projektu Universal Windows i skopiować istniejący kod do niego. Jeśli projekt uniwersalnej była używana dla pulpitu Windows 8.1 i Windows 8.1 Phone, projekt rozpoczyna się od dwóch różnych układów w XAML, ale zakończenia z jednym układ dynamiczny, który dostosowuje się do rozmiaru ekranu.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Port App Store Windows 8.1, aby platformy UWP

1. Jeśli jeszcze tego nie zrobiono, Otwórz swój projekt aplikacji Windows 8.1 w programie Visual Studio 2017, a następnie postępuj zgodnie z instrukcjami, aby zaktualizować pliku projektu.

   Musisz mieć zainstalowane **narzędzia Windows 8.1 w programie Visual Studio** Instalatora. Jeśli nie masz tych zainstalowane narzędzia uruchomić **programu Visual Studio** Instalatora z **programy i funkcje** oknie Wybierz **programu Visual Studio 2017**, a w oknie Ustawienia wybierz pozycję **Zmodyfikować**. Znajdź **narzędzia Windows 8.1**, upewnij się, że jest ono zaznaczone, a wybierz **OK**.

2. Otwórz **właściwości projektu** okna, a następnie w obszarze **C++** > **ogólne**ustaw **zestawu narzędzi platformy** do **wersji 141**, zestaw narzędzi dla programu Visual Studio 2017.

3. Skompiluj projekt jako projekt Windows 8.1 i rozwiązać wszelkie błędy kompilacji. Wszelkie błędy na tym etapie, są prawdopodobnie ze względu na istotne zmiany w narzędzia do kompilacji i bibliotek. Zobacz [Visual C++ — Historia latach 2003 – 2015 zmian](../porting/visual-cpp-change-history-2003-2015.md) uzyskać szczegółowy opis zmiany, które mogłyby wpłynąć na kod.

   Gdy projekt jest kompilowany prawidłowo, można przystąpić do portu do Universal Windows (Windows 10).

4. Utwórz nowy projekt aplikacji uniwersalnej Windows przy użyciu pustego szablonu. Warto nadać mu taką samą nazwę jak istniejącego projektu, mimo że w tym projektów musi być w różnych katalogach.

5. Zamknij rozwiązanie, a następnie używając **Eksplorator Windows** lub wiersza polecenia, kopiowania plików kodu (za pomocą rozszerzenia .cpp i .h, .xaml) z usługi Windows 8.1 projekt w tym samym folderze co plik projektu (.vcxproj) dla projektu utworzony w kroku 1. Nie Kopiuj plik Package.appxmanifest i jeśli masz osobnego kodu dla Windows 8.1 pulpitu i telefonu, wybierz jeden z nich do portu pierwszy (będziesz mieć wykonania dodatkowych czynności później, aby dostosować je do drugiego). Pamiętaj, aby kopiowanie i podfoldery i ich zawartość. Jeśli zostanie wyświetlony monit, wybierz opcję Zastąp wszystkie pliki o takich samych nazwach.

6. Ponownie otwórz rozwiązanie, a następnie wybierz **Dodaj** > **istniejący element** z menu skrótów dla węzła projektu. Zaznacz wszystkie pliki, które zostały skopiowane, z wyjątkiem tych, które są już częścią projektu.

   Sprawdź wszystkie podfoldery i upewnij się dodać pliki w nich także.

7. Jeśli nie używasz tej samej nazwie co stary projekt, otwórz plik Package.appxmanifest i zaktualizuj **punktu wejścia** aby odzwierciedlić nazwę przestrzeni nazw `App` klasy.

   **Punktu wejścia** polem w pliku Package.appxmanifest zawiera nazwę zakresu `App` klasy, która zawiera obszar nazw, który zawiera `App` klasy. Podczas tworzenia projektu Windows Universal przestrzeni nazw jest ustawiona na nazwę projektu. To różni się od co to jest w plikach, skopiowane z starego projektu, należy zaktualizować jednego lub drugiego, aby były zgodne.

8. Skompiluj projekt i rozwiązać wszelkie błędy kompilacji, ze względu na istotne zmiany między różnymi wersjami z zestawu Windows SDK.

9. Uruchom projekt, na komputerze lokalnym. Sprawdź, czy nie wystąpiły żadne błędy wdrożenia i że układ aplikacji wygląda uzasadnione i czy działa ona prawidłowo na pulpicie.

10. Jeśli masz pliki osobnego kodu i .xaml na innym urządzeniu, takie jak Windows Phone 8.1, bada ten kod i zidentyfikować, gdzie różni się od standardowych urządzeniami. Jeśli różnica polega tylko w układzie, można użyć **Visual State Manager** w języku xaml, aby dostosować wyświetlanie w zależności od rozmiaru ekranu. Aby poznać inne różnice używając sekcje warunków w kodzie za pomocą następujących instrukcji #if.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   Te instrukcje odpowiednio mają zastosowanie do aplikacji platformy UWP, Windows Phone Store aplikacji, zarówno lub żadna (klasycznej Win32 tylko dla komputerów stacjonarnych). Te makra są dostępne tylko w Windows SDK 8.1 i nowszych wersjach, więc jeśli kod musi mieć formę skompilowaną przy użyciu wcześniejszych wersji zestawu Windows SDK lub dla innych platform, oprócz Windows, a następnie należy również rozważyć, tak że żaden z nich są zdefiniowane.

11. Uruchamianie i debugowanie aplikacji na emulator lub urządzenie fizyczne, dla każdego typu urządzenia, którą obsługuje aplikacja. Aby uruchomić emulator, musisz uruchomić program Visual Studio na komputerze fizycznym, a nie maszynę wirtualną.

## <a name="BK_81Component"></a> Przenoszenie składnika wykonawczego Windows 8.1 do platformy uniwersalnej systemu Windows

Jeśli masz bibliotekę DLL lub składnik środowiska wykonawczego Windows, który już współdziała z aplikacjami Windows 8.1 Store służy tej procedury można pobrać składnika lub biblioteki DLL, Praca z platformy uniwersalnej systemu Windows i Windows 10. Podstawowa procedura polega na utworzenie nowego projektu, a następnie skopiować kod do niego.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Port składnika wykonawczego Windows 8.1 do platformy uniwersalnej systemu Windows

1. W **nowy projekt** okna dialogowego w programie Visual Studio 2017, zlokalizuj **Windows Universal** węzła. Jeśli nie widzisz tego węzła, zainstaluj [Tools for Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903) pierwszy. Wybierz **składnika środowiska wykonawczego Windows** szablonu, nadaj nazwę składnika, a następnie wybierz **OK** przycisku. Nazwa składnika będzie służyć jako nazwa przestrzeni nazw, dzięki czemu możesz chcieć użyć takiej samej nazwie jak obszar nazw usługi starych projektów. Wymaga to tworzenia projektu w innym folderze ze starą. Jeśli wybierzesz inną nazwę, możesz zaktualizować nazwę przestrzeni nazw w plikach wygenerowanego kodu.

2. Zamknij projekt.

3. Skopiuj wszystkie pliki kodu (.cpp, .h, XAML itp.) z danego składnika Windows 8.1 do nowo utworzonego projektu. Nie Kopiuj plik manifestu Package.appx.

4. Tworzenie i usuń wszelkie błędy z powodu przełomowych zmian między różnymi wersjami z zestawu Windows SDK.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

W trakcie przenoszenia kodu do platformy uniwersalnej systemu Windows, mogą wystąpić różne błędy. Oto niektóre z możliwych problemów, które mogą wystąpić.

### <a name="project-configuration-issues"></a>Problemy z konfiguracją projektu

Być może występuje błąd:

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

W takim przypadku projektu nie jest kompilowany jako projekt Windows Universal. Sprawdź plik projektu i upewnij się, że ma właściwych elementów XML, które identyfikują projektu jako projektu Universal Windows. Następujące elementy powinien być obecny (numer wersji platformy docelowej mogą się różnić):

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Jeśli utworzono nowy projekt platformy uniwersalnej systemu Windows przy użyciu programu Visual Studio, nie powinien tego błędu.

## <a name="see-also"></a>Zobacz także

[Przewodnik przenoszenia Visual C++](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)