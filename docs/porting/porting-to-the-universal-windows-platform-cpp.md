---
title: Przenoszenie na platformę uniwersalną systemu Windows (C++)
ms.date: 10/23/2019
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: 9314cb564e792a7d4949d422a3942e9d46a23cb2
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627206"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Przenoszenie na platformę uniwersalną systemu Windows (C++)

W tym temacie znajdują się informacje dotyczące sposobu przenoszenia istniejącego C++ kodu na platformę aplikacji systemu Windows 10, platforma uniwersalna systemu Windows. To, co jest określane przez termin *uniwersalny* , jest to, że kod można uruchomić na dowolnym urządzeniu z systemem Windows 10. Tworzysz pojedynczy projekt i jeden interfejs użytkownika w języku XAML, który działa dobrze na dowolnym urządzeniu z systemem Windows 10. Funkcja układu dynamicznego w języku XAML pozwala na dostosowanie interfejsu użytkownika aplikacji do różnych rozmiarów wyświetlania.

Dokumentacja Centrum deweloperów systemu Windows zawiera Przewodnik przenoszenia Windows 8.1 aplikacji do platforma uniwersalna systemu Windows. Zobacz [przechodzenie z środowisko wykonawcze systemu Windows 8 do platformy UWP](/windows/uwp/porting/w8x-to-uwp-root). Chociaż przewodnik koncentruje się głównie C# na kodzie, większość wskazówek ma zastosowanie do C++. Poniższe procedury zawierają bardziej szczegółowe informacje. Zobacz również [przenoszenie z aplikacji klasycznej do platformy UWP](/windows/uwp/porting/desktop-to-uwp-migrate).

Ten temat zawiera następujące procedury dotyczące przenoszenia kodu do platformy UWP.

- [Przenoszenie aplikacji ze sklepu Windows 8.1 do platformy UWP](#BK_81StoreApp)

- [Przenoszenie składnika środowiska uruchomieniowego Windows 8.1 do platformy UWP](#BK_81Component)

Jeśli masz klasyczny plik Win32 DLL i chcesz go wywołać z aplikacji platformy UWP, możesz to zrobić. Za pomocą takich procedur można utworzyć warstwę interfejsu użytkownika platformy UWP dla istniejącej klasycznej C++ aplikacji klasycznej systemu Windows lub międzyplatformowego kodu w warstwie C++ standardowa. Zobacz [jak: korzystanie z istniejącego C++ kodu w aplikacji platforma uniwersalna systemu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md). 

## <a name="BK_81StoreApp"></a>Przenoszenie aplikacji ze sklepu Windows 8.1 do platformy UWP

Jeśli masz aplikację ze sklepu Windows 8.1, możesz użyć tej procedury, aby uzyskać dostęp do platformy UWP i wszystkich urządzeń z systemem Windows 10.  Dobrym pomysłem jest najpierw skompilowanie projektu przy użyciu programu Visual Studio 2019 jako projektu Windows 8.1, aby najpierw wyeliminować wszelkie problemy związane ze zmianami w kompilatorze i bibliotekach. Po wykonaniu tych czynności istnieją dwa sposoby konwertowania tego elementu na projekt platformy UWP systemu Windows 10. Najprostszym sposobem (zgodnie z opisem w poniższej procedurze) jest utworzenie uniwersalnego projektu systemu Windows i skopiowanie do niego istniejącego kodu. Jeśli używasz uniwersalnego projektu dla Windows 8.1 Desktop i Windows 8.1 Phone, projekt rozpocznie się z dwoma różnymi układami w języku XAML, ale kończy się jednym układem dynamicznym, który dostosowuje się do rozmiaru ekranu.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Aby przenieść aplikację ze sklepu Windows 8.1 do platformy UWP

1. Jeśli jeszcze tego nie zrobiono, Otwórz projekt aplikacji Windows 8.1 w programie Visual Studio 2017 i postępuj zgodnie z instrukcjami, aby uaktualnić plik projektu.

   Musisz zainstalować **narzędzia Windows 8.1 w Instalatorze programu Visual Studio** . Jeśli nie masz zainstalowanych narzędzi, uruchom Instalatora **programu Visual Studio** z okna **programy i funkcje** , wybierz **program Visual Studio 2017**, a następnie w oknie instalatora wybierz polecenie **Modyfikuj**. Znajdź **Windows 8.1 narzędzia**, upewnij się, że jest zaznaczone, a następnie wybierz **przycisk OK**.

1. Otwórz okno **właściwości projektu** , a w obszarze **C++**  > **Ogólne**Ustaw zestaw **narzędzi platformy** na **najnowsze 141**, zestawu narzędzi dla programu Visual Studio 2017.

1. Kompiluj projekt jako projekt Windows 8.1 i rozwiąż wszelkie błędy kompilacji. Wszelkie błędy na tym etapie prawdopodobnie są spowodowane istotnymi zmianami w narzędziach i bibliotekach kompilacji. Zobacz [historię C++ zmian wizualnych 2003-2015](../porting/visual-cpp-change-history-2003-2015.md) , aby uzyskać szczegółowy opis zmian, które mogą wpływać na kod.

   Gdy projekt zostanie prawidłowo skompilowany, możesz przystąpić do portów do uniwersalnego systemu Windows (Windows 10).

1. Utwórz nowy projekt aplikacji uniwersalnej systemu Windows przy użyciu pustego szablonu. Możesz chcieć nadać mu taką samą nazwę jak istniejący projekt, chociaż należy to zrobić, aby projekty były w różnych katalogach.

1. Zamknij rozwiązanie, a następnie za pomocą **Eksploratora Windows** lub wiersza polecenia skopiuj pliki kodu (z rozszerzeniami. cpp,. h i. XAML) z projektu Windows 8.1 do tego samego folderu, w którym znajduje się plik projektu (. vcxproj) dla projektu utworzonego w kroku 1. Nie Kopiuj pliku Package. appxmanifest, a jeśli masz oddzielny kod dla Windows 8.1 pulpitu i telefonu, wybierz jeden z nich do portów (należy wykonać kilka zadań później, aby dostosować się do innych). Pamiętaj o skopiowaniu i podfolderach oraz ich zawartości. Jeśli zostanie wyświetlony monit, wybierz, aby zastąpić wszystkie pliki ze zduplikowanymi nazwami.

1. Otwórz ponownie rozwiązanie i wybierz opcję **dodaj** > **istniejący element** z menu skrótów dla węzła projektu. Zaznacz wszystkie skopiowane pliki, z wyjątkiem tych, które są już częścią projektu.

   Sprawdź wszystkie podfoldery i upewnij się, że pliki również zostały dodane.

1. Jeśli nie używasz tej samej nazwy projektu, co stary projekt, Otwórz plik Package. appxmanifest i zaktualizuj **punkt wejścia** , aby odzwierciedlał nazwę przestrzeni nazw dla klasy `App`.

   Pole **punkt wejścia** w pliku Package. appxmanifest zawiera nazwę zakresu dla klasy `App`, która obejmuje przestrzeń nazw, która zawiera klasę `App`. Podczas tworzenia projektu uniwersalnego systemu Windows przestrzeń nazw jest ustawiana na nazwę projektu. Jeśli różni się od plików, które zostały skopiowane ze starego projektu, należy zaktualizować jeden lub drugi w celu dopasowania.

1. Kompilowanie projektu i rozwiązywanie wszelkich błędów kompilacji z powodu istotnych zmian między różnymi wersjami Windows SDK.

1. Uruchom projekt na pulpicie lokalnym. Sprawdź, czy nie występują błędy wdrażania i czy układ aplikacji wygląda prawidłowo i czy działa poprawnie na pulpicie.

1. Jeśli masz osobne pliki kodu i. XAML dla innego urządzenia, takie jak Windows Phone 8,1, sprawdź ten kod i zidentyfikuj, gdzie różni się od standardowego urządzenia. Jeśli różnica dotyczy tylko układu, można użyć **Menedżera stanu wizualnego** w XAML, aby dostosować wyświetlanie w zależności od rozmiaru ekranu. Aby uzyskać inne różnice, można użyć sekcji warunków w kodzie, korzystając z poniższych instrukcji #if.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   Te instrukcje dotyczą odpowiednio aplikacji platformy UWP, aplikacji ze sklepu Windows Phone, obu lub nie (tylko klasyczny pulpit Win32). Te makra są dostępne tylko w Windows SDK 8,1 i nowszych, więc jeśli kod wymaga skompilowania ze starszymi wersjami Windows SDK lub dla innych platform oprócz systemu Windows, należy rozważyć również przypadek, w którym żaden z nich nie jest zdefiniowany.

1. Uruchamianie i debugowanie aplikacji na emulatorze lub urządzeniu fizycznym dla każdego typu urządzenia obsługiwanego przez aplikację. Aby uruchomić emulator, należy uruchomić program Visual Studio na komputerze fizycznym, a nie na maszynie wirtualnej.

## <a name="BK_81Component"></a>Przenoszenie składnika środowiska uruchomieniowego Windows 8.1 do platformy UWP

Jeśli masz bibliotekę DLL lub składnik środowisko wykonawcze systemu Windows, który już działa z aplikacjami ze sklepu Windows 8.1, możesz użyć tej procedury, aby pobrać składnik lub bibliotekę DLL pracującą z platformy UWP i Windows 10. Podstawową procedurą jest utworzenie nowego projektu i skopiowanie do niego kodu.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Aby przenieść składnik środowiska uruchomieniowego Windows 8.1 do platformy UWP

1. W oknie dialogowym **Nowy projekt** w programie Visual Studio 2017 zlokalizuj węzeł **uniwersalny systemu Windows** . Jeśli ten węzeł nie jest widoczny, najpierw zainstaluj [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) . Wybierz szablon **składnika Środowisko wykonawcze systemu Windows** , nadaj nazwę składnikowi, a następnie wybierz przycisk **OK** . Nazwa składnika zostanie użyta jako nazwa przestrzeni nazw, więc możesz chcieć użyć takiej samej nazwy, jak przestrzeń nazw starych projektów. Wymaga to utworzenia projektu w innym folderze niż stary. Jeśli wybierzesz inną nazwę, możesz zaktualizować nazwę przestrzeni nazw w wygenerowanych plikach kodu.

1. Zamknij projekt.

1. Skopiuj wszystkie pliki kodu (. cpp,. h,. xaml itp.) ze składnika Windows 8.1 do nowo utworzonego projektu. Nie Kopiuj pliku Package. appxmanifest.

1. Kompiluj i rozwiązywaj wszelkie błędy z powodu istotnych zmian między różnymi wersjami Windows SDK.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Podczas procesu przenoszenia kodu do platformy UWP mogą wystąpić różne błędy. Poniżej przedstawiono niektóre możliwe problemy.

### <a name="project-configuration-issues"></a>Problemy z konfiguracją projektu

Może zostać wyświetlony komunikat o błędzie:

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

W takim przypadku projekt nie jest kompilowany jako projekt uniwersalny systemu Windows. Sprawdź plik projektu i upewnij się, że zawiera on poprawne elementy XML, które identyfikują projekt jako uniwersalny projekt systemu Windows. Powinny być obecne następujące elementy (numer wersji platformy docelowej może być różny):

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Jeśli utworzono nowy projekt platformy UWP za pomocą programu Visual Studio, ten błąd nie powinien być widoczny.

## <a name="see-also"></a>Zobacz także

[Przewodnik C++ po przewoźnyu wizualnym](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)