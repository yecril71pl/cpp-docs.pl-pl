---
title: Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio
description: Jak nawiązać połączenie ze zdalnym komputerem z systemem Linux lub podsystemem Windows dla systemu Linux C++ z wnętrza projektu programu Visual Studio.
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518221"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range="vs-2017"

Projekt systemu Linux można skonfigurować tak, aby był przeznaczony dla maszyny zdalnej lub podsystemu Windows w systemie Linux (WSL). Dla obu maszyn zdalnych i WSL należy skonfigurować połączenie zdalne w programie Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Projekt systemu Linux można skonfigurować tak, aby był przeznaczony dla maszyny zdalnej lub podsystemu Windows w systemie Linux (WSL). W przypadku maszyny zdalnej należy skonfigurować połączenie zdalne w programie Visual Studio. Aby nawiązać połączenie z usługą WSL, przejdź do sekcji [łączenie z WSL](#connect-to-wsl) .

::: moniker-end

::: moniker range=">=vs-2017"

W przypadku korzystania z połączenia zdalnego program Visual Studio C++ kompiluje projekty systemu Linux na maszynie zdalnej. Nie ma znaczenia, czy jest to maszyna fizyczna, maszyna wirtualna w chmurze lub WSL.
Aby skompilować projekt, program Visual Studio kopiuje kod źródłowy na zdalny komputer z systemem Linux. Następnie kod zostanie skompilowany na podstawie ustawień programu Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Program Visual Studio 2019 w wersji 16,5 i nowszej obsługuje również bezpieczne połączenia kryptograficzne zgodne z systemami Linux (Federal Information Processing Standard 140-2). Aby użyć połączenia zgodnego ze standardem FIPS, wykonaj kroki opisane w sekcji [Konfigurowanie bezpiecznego zdalnego systemu Linux zgodnego ze standardem FIPS](set-up-fips-compliant-secure-remote-linux-development.md) .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Skonfiguruj serwer SSH w systemie zdalnym

Jeśli protokół SSH nie został jeszcze skonfigurowany i uruchomiony w systemie Linux, wykonaj następujące kroki, aby go zainstalować. W przykładach w tym artykule użyto Ubuntu 18,04 LTS z OpenSSH Server 7,6. Jednak instrukcje powinny być takie same dla każdego dystrybucjiu, w którym jest używana najnowsza wersja OpenSSH.

1. W systemie Linux Zainstaluj i uruchom serwer OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Jeśli chcesz, aby serwer SSH był uruchamiany automatycznie podczas uruchamiania systemu, włącz go przy użyciu systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Skonfiguruj połączenie zdalne

1. W programie Visual Studio wybierz pozycję **narzędzia > opcje** na pasku menu, aby otworzyć okno dialogowe **Opcje** . Następnie wybierz pozycję **Międzyplatformowe > Menedżer połączeń** , aby otworzyć okno dialogowe Menedżera połączeń.

   Jeśli nie skonfigurowano połączenia w programie Visual Studio przed rozpoczęciem kompilowania projektu po raz pierwszy, program Visual Studio otwiera okno dialogowe Menedżera połączeń.

1. W oknie dialogowym Menedżer połączeń wybierz przycisk **Dodaj** , aby dodać nowe połączenie.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W każdym scenariuszu zostanie wyświetlone okno **łączenie z systemem zdalnym** .

   ![Połącz z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Entry | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, na którym działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Obsługiwane są zarówno hasło, jak i klucz prywatny
   | **Hasło**            | Hasło do podanej nazwy użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego został utworzony na potrzeby połączenia SSH
   | **Danym**          | Hasło użyte z wybranym powyżej kluczem prywatnym

   Do uwierzytelniania można użyć hasła lub pliku klucza i hasła. W przypadku wielu scenariuszy programistycznych uwierzytelnianie hasła jest wystarczające, ale pliki kluczy są bezpieczniejsze. Jeśli masz już parę kluczy, można użyć jej ponownie. Obecnie program Visual Studio obsługuje tylko klucze RSA i DSA dla połączeń zdalnych.

1. Wybierz przycisk **Połącz** , aby podjąć próbę nawiązania połączenia z komputerem zdalnym.

   Jeśli połączenie powiedzie się, program Visual Studio skonfiguruje funkcję IntelliSense do używania zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wprowadzania, które należy zmienić, są opisane na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Jeśli używasz plików kluczy do uwierzytelniania, upewnij się, że serwer SSH maszyny docelowej jest uruchomiony i skonfigurowany prawidłowo.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Rejestrowanie dla połączeń zdalnych

   Możesz włączyć rejestrowanie, aby pomóc w rozwiązywaniu problemów z połączeniami. Na pasku menu wybierz pozycję **narzędzia > opcje**. W oknie dialogowym **Opcje** wybierz pozycję **Rejestrowanie > Międzyplatformowe**:

   ![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

   Dzienniki obejmują połączenia, wszystkie polecenia wysyłane do maszyny zdalnej (ich tekst, kod zakończenia i czas wykonywania) oraz wszystkie dane wyjściowe z programu Visual Studio do powłoki. Rejestrowanie działa w przypadku dowolnego projektu CMake na wielu platformach lub w programie Visual Studio opartym na programie MSBuild.

   Można skonfigurować dane wyjściowe, aby przejść do pliku lub w okienku **rejestrowania między platformami** w oknie dane wyjściowe. W przypadku projektów systemu Linux opartych na programie MSBuild polecenia programu MSBuild wysyłane do maszyny zdalnej nie są kierowane do **okno dane wyjściowe** , ponieważ są emitowane poza procesem. Zamiast tego są one rejestrowane w pliku z prefiksem "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Narzędzie wiersza polecenia dla Menedżera połączeń  

**Visual studio 2019 w wersji 16,5 lub nowszej**: ConnectionManager. exe to narzędzie wiersza polecenia do zarządzania połączeniami zdalnego tworzenia poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi nowej maszyny deweloperskiej. Można też użyć go do skonfigurowania programu Visual Studio na potrzeby ciągłej integracji. Przykłady i kompletne odwołanie do polecenia ConnectionManager można znaleźć w temacie [ConnectionManager Reference](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Przekazywanie portów TCP

Obsługa systemu Linux w programie Visual Studio ma zależność od przekazywania portów TCP. Jeśli przekazanie portów TCP jest wyłączone w systemie zdalnym, ma to na **rsync** i **serwera gdbserver** . Jeśli ma to wpływ na tę zależność, możesz przegłosować ten [bilet sugestii](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) w społeczności deweloperów.

rsync jest używany przez projekty systemu Linux oparte na programie MSBuild i projekty CMake do [kopiowania nagłówków z zdalnego komputera do systemu Windows do użycia przez funkcję IntelliSense](configure-a-linux-project.md#remote_intellisense). Gdy nie można włączyć przekazywania portów TCP, wyłącz automatyczne pobieranie nagłówków zdalnych. Aby go wyłączyć, użyj **narzędzi > opcje > Międzyplatformowe > Menedżer połączeń > zdalnych nagłówków IntelliSense**. Jeśli system zdalny nie ma włączonego przekazywania portów TCP, zobaczysz ten błąd, jeśli pobieranie zdalnych nagłówków dla funkcji IntelliSense rozpocznie się:

![Błąd nagłówków](media/port-forwarding-headers-error.png)

rsync jest również używany przez wsparcie CMake programu Visual Studio do kopiowania plików źródłowych do systemu zdalnego. Jeśli nie możesz włączyć przekazywania portów TCP, możesz użyć protokołu SFTP jako metody źródła kopiowania zdalnego. protokół SFTP jest często wolniejszy niż rsync, ale nie ma zależności od przekazywania portów TCP. Metodami kopiowania zdalnego można zarządzać za pomocą właściwości **remoteCopySourcesMethod** w [Edytorze ustawień CMAKE](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Jeśli przekazywanie portów TCP jest wyłączone w systemie zdalnym, w oknie danych wyjściowych CMake zostanie wyświetlony komunikat o błędzie podczas pierwszego uruchomienia rsync.

![Błąd rsync](media/port-forwarding-copy-error.png)

serwera gdbserver może służyć do debugowania na urządzeniach osadzonych. Jeśli nie możesz włączyć przekazywania portów TCP, musisz użyć GDB dla wszystkich scenariuszy zdalnego debugowania. GDB jest używana domyślnie podczas debugowania projektów w systemie zdalnym.

## <a name="connect-to-wsl"></a>Nawiązywanie połączenia z usługą WSL

::: moniker-end

::: moniker range="vs-2017"

W programie Visual Studio 2017 należy wykonać te same czynności, aby nawiązać połączenie z usługą WSL, która jest używana na potrzeby zdalnego komputera z systemem Linux. Użyj **nazwy hosta** **localhost** .

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 w wersji 16,1 dodano natywną C++ obsługę programu z [podsystemem Windows dla systemu Linux (WSL)](/windows/wsl/about). Oznacza to, że można kompilować i debugować lokalną instalację WSL bezpośrednio. Nie trzeba już dodawać połączenia zdalnego ani konfigurować protokołu SSH. Szczegółowe informacje na [temat sposobu instalowania WSL](/windows/wsl/install-win10) można znaleźć tutaj.

Aby skonfigurować instalację programu WSL do pracy z programem Visual Studio, potrzebne są następujące narzędzia: w zatoce lub Clang, GDB, marka, rsync i zip. Można je zainstalować na dystrybucje, które używają apt przy użyciu tego polecenia, które również instaluje kompilator g + +:

```bash
sudo apt install g++ gdb make rsync zip
```

Aby uzyskać więcej informacji, zobacz [pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

Aby skonfigurować projekt programu MSBuild dla programu WSL, zobacz [Konfigurowanie projektu systemu Linux](configure-a-linux-project.md). Aby skonfigurować projekt CMake dla WSL, zobacz [Configure a Linux CMAKE Project](cmake-linux-project.md). Aby wykonać instrukcje krok po kroku dotyczące tworzenia prostej aplikacji konsolowej z WSL, zapoznaj się z tym wpisem na blogu wprowadzającym w [ C++ programie Visual Studio 2019 i podsystemem Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Konfigurowanie\ projektu systemu Linux](configure-a-linux-project.md)
[Konfigurowanie\ projektu systemu Linux CMAKE](cmake-linux-project.md)
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)
