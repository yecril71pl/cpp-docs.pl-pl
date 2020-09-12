---
title: Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS
ms.date: 10/17/2019
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
ms.openlocfilehash: 26dea080f3d3f05885f348dcaf1c66a0db2a36b5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041994"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS

Możesz użyć programu Visual Studio z **programowaniem aplikacji mobilnych dla wielu platform za pomocą narzędzi języka C++** , aby edytować, debugować i wdrażać kod systemu iOS w symulatorze systemu iOS lub na urządzeniu z systemem iOS. Jednak ze względu na ograniczenia licencjonowania kod musi być skompilowany i uruchamiany zdalnie na komputerze Mac. Aby kompilować i uruchamiać aplikacje dla systemu iOS przy użyciu programu Visual Studio, należy skonfigurować i skonfigurować agenta zdalnego, [vcremote](https://www.npmjs.com/package/vcremote)na komputerze Mac. Agent zdalny obsługuje żądania kompilacji z programu Visual Studio i uruchamia aplikację na urządzeniu z systemem iOS podłączonym do komputera Mac lub w symulatorze systemu iOS na komputerze Mac.

> [!NOTE]
> Aby uzyskać informacje na temat korzystania z usług Mac hostowanych w chmurze zamiast komputerów Mac, zobacz [Konfigurowanie programu Visual Studio do nawiązywania połączenia z hostowanym komputerem Mac w chmurze](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017&preserve-view=true#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Instrukcje służą do kompilowania przy użyciu Visual Studio Tools Apache Cordova. Aby użyć instrukcji do kompilowania przy użyciu języka C++, podstaw `vcremote` `remotebuild` .

Po zainstalowaniu narzędzi do kompilowania przy użyciu systemu iOS zapoznaj się z tym artykułem, aby szybko skonfigurować i zaktualizować agenta zdalnego dla tworzenia aplikacji dla systemu iOS w programie Visual Studio i na komputerze Mac.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zainstalować i użyć agenta zdalnego do opracowania kodu dla systemu iOS, należy najpierw spełnić te wymagania wstępne:

- Komputer Mac z systemem macOS Mojave w wersji 10,14 lub nowszej

- [Identyfikator Apple ID](https://appleid.apple.com/)

- Aktywne konto [programu Apple Developer](https://developer.apple.com/programs/)

   Możesz uzyskać bezpłatne konto, które umożliwia aplikacjom lokalnym na urządzeniu z systemem iOS testowanie tylko, ale nie do dystrybucji.

- [Xcode](https://developer.apple.com/xcode/downloads/) w wersji 10.2.1 lub nowszej

   Xcode można pobrać ze sklepu z aplikacjami.

- Narzędzia wiersza polecenia Xcode

   Aby zainstalować narzędzia wiersza polecenia Xcode, Otwórz aplikację terminala na komputerze Mac i wprowadź następujące polecenie:

   `xcode-select --install`

- Konto Apple ID skonfigurowane w Xcode jako tożsamość podpisująca do podpisywania aplikacji

   Aby wyświetlić lub ustawić tożsamość podpisywania w programie Xcode, otwórz menu **Xcode** i wybierz polecenie **Preferences (Preferencje**). Wybierz pozycję **konta** i wybierz swój identyfikator Apple ID, a następnie wybierz przycisk **Wyświetl szczegóły** . Aby uzyskać szczegółowe instrukcje, zobacz [Dodawanie konta Apple ID](https://help.apple.com/xcode/mac/current/#/devaf282080a) .

   Aby uzyskać szczegółowe informacje na temat wymagań dotyczących podpisywania, zobacz [co to jest podpisywanie aplikacji](https://help.apple.com/xcode/mac/current/#/dev3a05256b8).

- Jeśli używasz urządzenia z systemem iOS do tworzenia aplikacji, profil aprowizacji skonfigurowany w Xcode dla urządzenia

   Xcode zapewnia automatyczne podpisywanie, gdy w razie potrzeby tworzy certyfikaty podpisywania. Aby uzyskać szczegółowe informacje na temat Xcode automatycznego podpisywania, zobacz [Automatyczne podpisywanie](https://help.apple.com/xcode/mac/current/#/dev80cc24546).

   Jeśli chcesz przeprowadzić ręczne podpisywanie, musisz utworzyć profil aprowizacji dla swojej aplikacji. Aby uzyskać szczegółowe informacje na temat tworzenia profilów aprowizacji, zobacz [Tworzenie profilu aprowizacji programistycznej](https://help.apple.com/developer-account/#/devf2eb157f8).

- [Node.js](https://nodejs.org/) wersja 12.14.1 i wersja npm 6.13.4

   Zainstaluj wersję 12.14.1 Node.js na komputerze Mac. Jeśli instalujesz pakiet Node.js, powinien on mieć npm w wersji 6.13.4. Inne wersje Node.js i npm mogą nie obsługiwać niektórych modułów używanych w agencie zdalnym `vcremote` , co może spowodować `vcremote` Niepowodzenie instalacji. Zalecamy zainstalowanie Node.js przy użyciu Menedżera pakietów, takiego jak [Menedżer wersji węzła](https://nodejs.org/en/download/package-manager/#nvm). Należy unikać używania polecenia `sudo` , aby zainstalować Node.js, ponieważ podczas korzystania z programu nie można zainstalować niektórych modułów `sudo` .

## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> Zainstaluj agenta zdalnego dla systemu iOS

W przypadku instalowania aplikacji mobilnych przy użyciu obciążenia języka C++ Program Visual Studio może komunikować się z usługą [vcremote](https://www.npmjs.com/package/vcremote), zdalnym agentem uruchomionym na komputerze Mac w celu transferu plików, kompilowania i uruchamiania w aplikacjach systemu iOS oraz wysyłania poleceń debugowania.

Przed zainstalowaniem agenta zdalnego upewnij się, że spełniono [wymagania wstępne](#prerequisites) i wykonano kroki instalacji w temacie [Instalowanie międzyplatformowego opracowywania aplikacji mobilnych za pomocą języka C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> Aby pobrać i zainstalować agenta zdalnego

- W aplikacji terminalowej na komputerze Mac Sprawdź, czy wersja Node.js aktualnie używana jest wymagana wersja 12.14.1. Aby sprawdzić wersję, uruchom polecenie:

  `node -v`
  
  Jeśli nie jest to właściwa wersja, może być konieczne wykonanie instrukcji instalacji Node.js w sekcji wymagania wstępne. Następnie ponownie uruchom Node.js.

- Po sprawdzeniu, czy wymagane Node.js jest w użyciu, Uruchom to polecenie, aby zainstalować program vcremote w wersji Node.js:

   `npm install -g --unsafe-perm vcremote`

   Przełącznik instalacji globalnej (**-g**) jest zalecany, ale nie jest wymagany. Jeśli nie używasz globalnego przełącznika instalacji, vcremote zostanie zainstalowany w ramach bieżącej aktywnej ścieżki w aplikacji terminalowej.

   Podczas instalacji program `vcremote` jest instalowany, a na komputerze Mac jest aktywowany Tryb dewelopera. [Oprogramowania Homebrew](https://brew.sh/) i dwa pakiety npm `vcremote-lib` `vcremote-utils` są również zainstalowane. Po zakończeniu instalacji można bezpiecznie zignorować wszystkie ostrzeżenia dotyczące pominiętych zależności opcjonalnych.

   > [!NOTE]
   > Aby zainstalować oprogramowania homebrew, musisz mieć dostęp do programu sudo (Administrator). Jeśli musisz zainstalować `vcremote` program bez sudo, możesz zainstalować oprogramowania Homebrew ręcznie w lokalizacji usr/local i dodać jej folder bin do ścieżki. Aby uzyskać więcej informacji, zapoznaj się z [dokumentacją oprogramowania Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Aby ręcznie włączyć tryb dewelopera, wprowadź to polecenie w aplikacji terminalowej: `DevToolsSecurity -enable`

W przypadku aktualizacji do nowej wersji programu Visual Studio należy również zaktualizować ją do bieżącej wersji agenta zdalnego. Aby zaktualizować agenta zdalnego, powtórz kroki, aby pobrać i zainstalować agenta zdalnego.

## <a name="start-the-remote-agent"></a><a name="Start"></a> Uruchom agenta zdalnego

Aby program Visual Studio mógł skompilować i uruchomić kod systemu iOS, Agent zdalny musi być uruchomiony. Program Visual Studio musi być sparowany z agentem zdalnym, aby mógł się komunikować. Domyślnie zdalny Agent jest uruchamiany w trybie połączenia zabezpieczonego, który wymaga, aby numer PIN został sparowany z programem Visual Studio.

### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> Aby uruchomić agenta zdalnego

- Z poziomu aplikacji terminalowej na komputerze Mac wpisz:

   `vcremote`

   To polecenie uruchamia agenta zdalnego przy użyciu domyślnego katalogu kompilacji programu `~/vcremote` . Aby uzyskać dodatkowe opcje konfiguracji, zobacz [Konfigurowanie zdalnego agenta na komputerze Mac](#ConfigureMac).

Przy pierwszym uruchomieniu agenta i za każdym razem, gdy tworzysz nowy certyfikat klienta, należy podać wymagane informacje, aby skonfigurować agenta w programie Visual Studio, w tym nazwę hosta, port i numer PIN.

![Użyj vcremote do wygenerowania bezpiecznego numeru PIN](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "Użyj vcremote do wygenerowania bezpiecznego numeru PIN")

Jeśli zamierzasz skonfigurować agenta zdalnego w programie Visual Studio przy użyciu nazwy hosta, Wyślij polecenie ping do komputera Mac z systemu Windows przy użyciu nazwy hosta, aby sprawdzić, czy jest osiągalny. W przeciwnym razie może być konieczne użycie tego adresu IP.

Wygenerowany kod PIN jest używany do jednorazowego użycia i jest prawidłowy tylko przez ograniczony czas. Jeśli program Visual Studio nie zostanie sparowany z agentem zdalnym przed upływem czasu, konieczne będzie wygenerowanie nowego numeru PIN. Aby uzyskać więcej informacji, zobacz [generowanie nowego numeru PIN zabezpieczeń](#GeneratePIN).

Agenta zdalnego można używać w trybie niezabezpieczonym. W trybie niezabezpieczonym Agent zdalny może być sparowany z Visual Studio bez numeru PIN.

#### <a name="to-disable-secured-connection-mode"></a>Aby wyłączyć tryb bezpiecznego połączenia

- Aby wyłączyć tryb bezpiecznego połączenia w programie `vcremote` , wprowadź to polecenie w aplikacji terminalowej na komputerze Mac:

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Aby włączyć tryb połączenia zabezpieczonego

- Aby włączyć tryb połączenia zabezpieczonego, wprowadź następujące polecenie:

   `vcremote --secure true`

Po uruchomieniu zdalnego agenta można go użyć z programu Visual Studio, dopóki nie zostanie zatrzymany.

#### <a name="to-stop-the-remote-agent"></a>Aby zatrzymać agenta zdalnego

- W oknie terminalu `vcremote` jest uruchomiony program, wpisz **Control** + **C**.

## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> Konfigurowanie agenta zdalnego w programie Visual Studio

Aby połączyć się z agentem zdalnym z poziomu programu Visual Studio, należy określić konfigurację zdalną w opcjach programu Visual Studio.

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Aby skonfigurować agenta zdalnego z programu Visual Studio

1. Jeśli Agent nie jest jeszcze uruchomiony na komputerze Mac, wykonaj kroki opisane w sekcji [Uruchamianie zdalnego agenta](#Start). Na komputerze Mac musi działać `vcremote` program Visual Studio w celu pomyślnego sparowania, połączenia i kompilowania projektu.

1. Na komputerze Mac Pobierz nazwę hosta lub adres IP komputera Mac.

   Adres IP można uzyskać za pomocą polecenia **ifconfig** w oknie terminalu. Użyj adresu inet podanego w ramach aktywnego interfejsu sieciowego.

1. Na pasku menu programu Visual Studio wybierz **Narzędzia**, **Opcje**.

1. W oknie dialogowym **Opcje** rozwiń pozycję **Międzyplatformowe**, **C++** i **iOS**.

1. W polach **Nazwa hosta** i **port** wprowadź wartości określone przez agenta zdalnego podczas jego uruchamiania. Nazwą hosta może być nazwa DNS lub adres IP komputera Mac. Domyślnym portem jest 3030.

   > [!NOTE]
   > Jeśli nie można wysłać polecenia ping do komputera Mac przy użyciu nazwy hosta, może być konieczne użycie adresu IP.

1. Jeśli używasz zdalnego agenta w domyślnym trybie bezpiecznego połączenia, zaznacz pole wyboru **bezpieczne** , a następnie wprowadź wartość numeru PIN określoną przez agenta zdalnego w polu **kod PIN** . Jeśli używasz zdalnego agenta w trybie niezabezpieczonego połączenia, wyczyść pole wyboru **bezpieczne** i pozostaw puste pole **numeru PIN** .

1. Wybierz **parę** , aby włączyć parowanie.

   ![Konfigurowanie połączenia vcremote dla kompilacji systemu iOS](../cross-platform/media/cppmdd-options-ios.png "Konfigurowanie połączenia vcremote dla kompilacji systemu iOS")

   Parowanie jest zachowywane do momentu zmiany nazwy hosta lub portu. Jeśli zmienisz nazwę hosta lub port w oknie dialogowym **Opcje** , aby cofnąć zmianę, wybierz przycisk **Przywróć** , aby przywrócić poprzednią parowanie.

   Jeśli parowanie nie powiedzie się, sprawdź, czy Agent zdalny działa, wykonując kroki opisane w temacie [Uruchamianie zdalnego agenta](#Start). Jeśli upłynął zbyt dużo czasu od momentu wygenerowania numeru PIN agenta zdalnego, wykonaj kroki opisane w sekcji [generowanie nowego numeru PIN zabezpieczeń](#GeneratePIN) na komputerze Mac, a następnie spróbuj ponownie. Jeśli używasz nazwy hosta dla komputera Mac, zamiast tego spróbuj użyć adresu IP w polu **Nazwa hosta** .

1. Zaktualizuj nazwę folderu w polu **zdalny katalog główny** , aby określić folder używany przez agenta zdalnego w katalogu głównym ( *~* ) na komputerze Mac. Domyślnie zdalny Agent jest wykorzystywany `/Users/<username>/vcremote` jako zdalny katalog główny.

1. Wybierz **przycisk OK** , aby zapisać ustawienia połączenia zdalnego parowania.

Program Visual Studio używa tych samych informacji do łączenia się z agentem zdalnym na komputerze Mac za każdym razem, gdy jest używany. Nie trzeba ponownie łączyć programu Visual Studio z agentem zdalnym, chyba że zostanie wygenerowany nowy certyfikat zabezpieczeń na komputerze Mac lub jego nazwa hosta lub adres IP.

## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Generuj nowy zabezpieczający kod PIN

Po pierwszym uruchomieniu zdalnego agenta wygenerowany kod PIN jest ważny przez ograniczoną ilość czasu — domyślnie 10 minut. Jeśli nie połączysz programu Visual Studio z agentem zdalnym przed upływem czasu, konieczne będzie wygenerowanie nowego numeru PIN.

### <a name="to-generate-a-new-pin"></a>Aby wygenerować nowy kod PIN

1. Zatrzymaj agenta lub Otwórz drugie okno aplikacji terminala na komputerze Mac i Użyj tego polecenia, aby wprowadzić polecenie.

1. Wprowadź to polecenie w aplikacji terminalowej:

   `vcremote generateClientCert`

   Agent zdalny generuje nowy tymczasowy numer PIN. Aby sparować program Visual Studio przy użyciu nowego numeru PIN, powtórz czynności opisane w sekcji [Konfigurowanie zdalnego agenta w programie Visual Studio](#ConfigureVS).

## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> Wygeneruj nowy certyfikat serwera

Ze względów bezpieczeństwa certyfikaty serwera, które kojarzą program Visual Studio z agentem zdalnym, są powiązane z adresem IP lub nazwą hosta komputera Mac. Jeśli te wartości zmienią się, należy wygenerować nowy certyfikat serwera, a następnie ponownie skonfigurować program Visual Studio przy użyciu nowych wartości.

### <a name="to-generate-a-new-server-certificate"></a>Aby wygenerować nowy certyfikat serwera

1. Zatrzymaj `vcremote` agenta.

1. Wprowadź to polecenie w aplikacji terminalowej:

   `vcremote resetServerCert`

1. Po wyświetleniu monitu o potwierdzenie wprowadź `Y` .

1. Wprowadź to polecenie w aplikacji terminalowej:

   `vcremote generateClientCert`

   To polecenie generuje nowy tymczasowy numer PIN.

1. Aby sparować program Visual Studio przy użyciu nowego numeru PIN, powtórz czynności opisane w sekcji [Konfigurowanie zdalnego agenta w programie Visual Studio](#ConfigureVS).

## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Konfigurowanie zdalnego agenta na komputerze Mac

Agenta zdalnego można skonfigurować przy użyciu różnych opcji wiersza polecenia. Na przykład można określić port do nasłuchiwania żądań kompilacji i określić maksymalną liczbę kompilacji do utrzymania w systemie plików. Domyślnie limit wynosi 10 kompilacji. Agent zdalny usunie kompilacje, które przekraczają maksymalną wartość przy zamykaniu.

### <a name="to-configure-the-remote-agent"></a>Aby skonfigurować agenta zdalnego

- Aby wyświetlić pełną listę poleceń agenta zdalnego, w aplikacji terminala wprowadź:

   `vcremote --help`

- Aby wyłączyć tryb bezpieczny i włączyć proste połączenia oparte na protokole HTTP, wprowadź:

   `vcremote --secure false`

   W przypadku korzystania z tej opcji Wyczyść pole wyboru **bezpieczne** i pozostaw pole **numeru PIN** puste podczas konfigurowania agenta w programie Visual Studio.

- Aby określić lokalizację plików agenta zdalnego, wprowadź:

   `vcremote --serverDir directory_path`

   gdzie *directory_path* to lokalizacja na komputerze Mac, w której mają zostać umieszczone pliki dziennika, kompilacje i certyfikaty serwera. Domyślnie ta lokalizacja to `/Users/<username>/vcremote` . Kompilacje są zorganizowane według numeru kompilacji w tej lokalizacji.

- Aby użyć procesu w tle do przechwytywania `stdout` i `stderr` do pliku o nazwie Server. log, wpisz:

   `vcremote > server.log 2>&1 &`

   Plik Server. log może pomóc w rozwiązywaniu problemów z kompilacją.

- Aby uruchomić agenta przy użyciu pliku konfiguracji zamiast parametrów wiersza polecenia, wpisz:

   `vcremote --config config_file_path`

   gdzie *config_file_path* jest ścieżką do pliku konfiguracji w formacie JSON. Opcje uruchamiania i ich wartości nie mogą zawierać kresek.

## <a name="troubleshoot-the-remote-agent"></a>Rozwiązywanie problemów z agentem zdalnym

### <a name="debugging-on-an-ios-device"></a>Debugowanie na urządzeniu z systemem iOS

Jeśli debugowanie na urządzeniu z systemem iOS nie działa, mogą wystąpić problemy z [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller)narzędzia, które jest używane do komunikowania się z urządzeniem z systemem iOS. To narzędzie jest zazwyczaj instalowane z oprogramowania Homebrew podczas instalacji programu `vcremote` . Wykonaj poniższe kroki jako obejście problemu.

Otwórz aplikację terminala i zaktualizuj `ideviceinstaller` i jej zależności, uruchamiając następujące polecenia w kolejności:

1. Upewnij się, że oprogramowania Homebrew został zaktualizowany

   `brew update`

1. Odinstalowywanie `libimobiledevice` i `usbmuxd`

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. Zainstaluj najnowszą wersję programu `libimobiledevice` i `usbmuxd`

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. Odinstaluj i zainstaluj ponownie `ideviceinstaller`

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

Sprawdź, czy program `ideviceinstaller` może komunikować się z urządzeniem, próbując wyświetlić listę aplikacji zainstalowanych na urządzeniu:

`ideviceinstaller -l`

Jeśli `ideviceinstaller` błędy nie mają dostępu do folderu `/var/db/lockdown` , Zmień uprawnienie dla tego folderu na:

`sudo chmod 777 /var/db/lockdown`

Następnie sprawdź ponownie, jeśli `ideviceinstaller` program może komunikować się z urządzeniem.

## <a name="see-also"></a>Zobacz także

- [Instalowanie środowiska opracowywania aplikacji mobilnych na wiele platform w języku C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
