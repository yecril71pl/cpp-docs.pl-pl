---
title: Łączenie się z docelowym systemem Linux w programie Visual Studio
description: Jak połączyć się ze zdalnym komputerem z systemem Linux lub podsystemem windows dla systemu Linux z wnętrza projektu Visual Studio C++.
ms.date: 01/17/2020
ms.openlocfilehash: 624dce6bb05e4f4a961628e0c6f455e11c14dff8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364363"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Łączenie się z docelowym systemem Linux w programie Visual Studio

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range="vs-2017"

Można skonfigurować projekt systemu Linux do kierowania na komputer zdalny lub podsystemu windows dla systemu Linux (WSL). Zarówno dla komputerów zdalnych, jak i dla WSL należy skonfigurować połączenie zdalne w programie Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Można skonfigurować projekt systemu Linux do kierowania na komputer zdalny lub podsystemu windows dla systemu Linux (WSL). W przypadku komputera zdalnego należy skonfigurować połączenie zdalne w programie Visual Studio. Aby połączyć się z WSL, przejdź do sekcji [Połącz z WSL.](#connect-to-wsl)

::: moniker-end

::: moniker range=">=vs-2017"

Podczas korzystania z połączenia zdalnego visual studio tworzy projekty systemu Linux języka C++ na komputerze zdalnym. Nie ma znaczenia, czy jest to maszyna fizyczna, maszyna wirtualna w chmurze lub WSL.
Aby utworzyć projekt, visual studio kopiuje kod źródłowy do zdalnego komputera z systemem Linux. Następnie kod zostanie skompilowany na podstawie ustawień programu Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 w wersji 16.5 i nowszych obsługuje również bezpieczne, federal information processing standard (FIPS) 140-2 zgodne z połączeniami kryptograficznymi z systemami Linux w celu zdalnego rozwoju. Aby użyć połączenia zgodnego ze standardem FIPS, wykonaj czynności opisane w sekcji [Konfigurowanie bezpiecznego zdalnego bezpieczeństwa linuuu operacyjnego zgodnego ze standardem FIPS.](set-up-fips-compliant-secure-remote-linux-development.md)

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Konfigurowanie serwera SSH w systemie zdalnym

Jeśli ssh nie jest jeszcze skonfigurowany i uruchomiony w systemie Linux, wykonaj następujące kroki, aby go zainstalować. Przykłady w tym artykule używają Ubuntu 18.04 LTS z serwerem OpenSSH w wersji 7.6. Jednak instrukcje powinny być takie same dla każdej dystrybucji przy użyciu umiarkowanie najnowszej wersji OpenSSH.

1. W systemie Linux zainstaluj i uruchom serwer OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Jeśli chcesz, aby serwer ssh uruchamiał się automatycznie po uruchomieniu systemu, włącz go za pomocą systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Konfigurowanie połączenia zdalnego

1. W programie Visual Studio wybierz pozycję **Narzędzia > opcje** na pasku menu, aby otworzyć okno dialogowe **Opcje.** Następnie wybierz **Międzyplatformowe > Menedżera połączeń,** aby otworzyć okno dialogowe Menedżera połączeń.

   Jeśli połączenie nie zostały wcześniej skonfigurowane w programie Visual Studio, podczas tworzenia projektu po raz pierwszy program Visual Studio otworzy okno dialogowe Menedżera połączeń.

1. W oknie dialogowym Menedżer połączeń wybierz przycisk **Dodaj,** aby dodać nowe połączenie.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W obu scenariuszach zostanie wyświetlone okno **Połącz z systemem zdalnym.**

   ![Łączenie się z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Portu**                | Port, na który działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Hasło i klucz prywatny są obsługiwane
   | **Hasło**            | Hasło wprowadzonej nazwy użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego utworzony dla połączenia ssh
   | **Hasło**          | Hasło używane z wybranym kluczem prywatnym powyżej

   Do uwierzytelniania można użyć hasła lub pliku klucza i hasła. W wielu scenariuszach rozwoju uwierzytelnianie hasłem jest wystarczające, ale pliki kluczy są bezpieczniejsze. Jeśli masz już parę kluczy, możesz ją użyć ponownie. Obecnie program Visual Studio obsługuje tylko klucze RSA i DSA dla połączeń zdalnych.

1. Wybierz przycisk **Połącz,** aby spróbować nawiązać połączenie z komputerem zdalnym.

   Jeśli połączenie zakończy się pomyślnie, visual studio konfiguruje IntelliSense używać zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wejścia, które należy zmienić, są zaznaczone na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Jeśli używasz plików kluczy do uwierzytelniania, upewnij się, że serwer SSH komputera docelowego jest uruchomiony i skonfigurowany poprawnie.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Rejestrowanie połączeń zdalnych

   Rejestrowanie można włączyć, aby ułatwić rozwiązywanie problemów z połączeniem. Na pasku menu wybierz pozycję **Narzędzia > opcje**. W oknie dialogowym **Opcje** wybierz **pozycję Międzyplatformowy > Rejestrowanie:**

   ![Zdalne rejestrowanie](media/remote-logging-vs2019.png)

   Dzienniki obejmują połączenia, wszystkie polecenia wysyłane do komputera zdalnego (ich tekst, kod zakończenia i czas wykonywania) i wszystkie dane wyjściowe z programu Visual Studio do powłoki. Rejestrowanie działa dla dowolnego projektu CMake między platformami lub projektu systemu Linux opartego na systemie MSBuild w programie Visual Studio.

   Można skonfigurować dane wyjściowe, aby przejść do pliku lub do **okienka rejestrowania między platformami** w oknie Dane wyjściowe. W przypadku projektów systemu Linux opartych na systemie MSBuild polecenia MSBuild wysyłane do komputera zdalnego nie są kierowane do **okna wyjściowego,** ponieważ są emitowane poza procesem. Zamiast tego są one rejestrowane w pliku z prefiksem "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Narzędzie wiersza polecenia dla Menedżera połączeń  

**Visual Studio 2019 w wersji 16.5 lub nowszej:** ConnectionManager.exe jest narzędziem wiersza polecenia do zarządzania połączeniami zdalnego programowania poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi administracyjnej nowego komputera dewelopera. Lub można go użyć do skonfigurowania programu Visual Studio do ciągłej integracji. Przykłady i pełne odwołanie do polecenia ConnectionManager można znaleźć w [1944 roku.](connectionmanager-reference.md)  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Przekazywanie portów TCP

Obsługa systemu Linux w programie Visual Studio ma zależność od przekazywania portów TCP. Jeśli przekazywanie portów TCP jest wyłączone w systemie zdalnym, dotyczy **rsync** i **gdbserver.** Jeśli ta zależność ma na ciebie wpływ, możesz przegłosować ten [bilet sugestii](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) w społeczności deweloperów.

rsync jest używany zarówno przez projekty oparte na systemie Linux msbuild, jak i projekty CMake do [kopiowania nagłówków z systemu zdalnego do systemu Windows do użytku przez IntelliSense](configure-a-linux-project.md#remote_intellisense). Jeśli nie można włączyć przekazywania portów TCP, wyłącz automatyczne pobieranie zdalnych nagłówków. Aby ją wyłączyć, użyj **opcji narzędzia > > Cross Platform > Connection Manager > Remote Headers IntelliSense Manager**. Jeśli system zdalny nie ma włączonego przekazywania portów TCP, ten błąd zostanie wyświetlony po rozpoczęciu pobierania nagłówków zdalnych dla intellisense:

![Błąd nagłówków](media/port-forwarding-headers-error.png)

rsync jest również używany przez cMake obsługi programu Visual Studio do kopiowania plików źródłowych do systemu zdalnego. Jeśli nie można włączyć przekazywania portów TCP, możesz użyć sftp jako metody zdalnych źródeł kopiowania. sftp jest często wolniejszy niż rsync, ale nie ma zależności od przekazywania portów TCP. Metodę zdalnych źródeł kopiowania można zarządzać za pomocą właściwości **remoteCopySourcesMethod** w [Edytorze ustawień CMake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Jeśli przekazywanie portów TCP jest wyłączone w systemie zdalnym, w oknie wyjściowym CMake po raz pierwszy zostanie wyświetlony błąd w oknie wyjściowym CMake przy pierwszym wywołaniu rsync.

![Błąd Rsync](media/port-forwarding-copy-error.png)

gdbserver może być używany do debugowania na urządzeniach wbudowanych. Jeśli nie można włączyć przekazywania portów TCP, należy użyć gdb dla wszystkich scenariuszy zdalnego debugowania. gdb jest używany domyślnie podczas debugowania projektów w systemie zdalnym.

## <a name="connect-to-wsl"></a>Łączenie się z wsl

::: moniker-end

::: moniker range="vs-2017"

W programie Visual Studio 2017 należy wykonać te same kroki, aby połączyć się z WSL, jak używasz dla zdalnego komputera z systemem Linux. Użyj **localhost** dla **nazwy hosta**.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 w wersji 16.1 dodał natywną obsługę używania języka C++ z [podsystemem Windows dla systemu Linux (WSL).](/windows/wsl/about) Oznacza to, że można tworzyć i debugować na lokalnej instalacji WSL bezpośrednio. Nie trzeba już dodawać połączenia zdalnego ani konfigurować SSH. Szczegółowe informacje na temat [instalacji WSL](/windows/wsl/install-win10) można znaleźć tutaj.

Aby skonfigurować instalację WSL do pracy z programem Visual Studio, potrzebne są następujące narzędzia: gcc lub clang, gdb, make, ninja-build (wymagane tylko dla projektów CMake przy użyciu programu Visual Studio 2019 w wersji 16.6 lub nowszej), rsync i zip. Można je zainstalować na dystrybucjach, które używają apt za pomocą tego polecenia, które również instaluje kompilator g++:

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

Aby uzyskać więcej informacji, zobacz [Pobieranie, instalowanie i konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

Aby skonfigurować projekt MSBuild dla WSL, zobacz [Konfigurowanie projektu systemu Linux](configure-a-linux-project.md). Aby skonfigurować projekt CMake dla WSL, zobacz [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md). Aby postępować zgodnie z instrukcjami krok po kroku dotyczącymi tworzenia prostej aplikacji konsoli z WSL, zapoznaj się z tym wpisem w blogu wprowadzającym w [języku C++ w programie Visual Studio 2019 i podsystemie Windows dla systemu Linux (WSL).](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)\
[Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)
