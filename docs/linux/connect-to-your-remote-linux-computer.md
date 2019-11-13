---
title: Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio
description: Jak nawiązać połączenie ze zdalnym komputerem z systemem Linux lub podsystemem Windows dla systemu Linux C++ z wnętrza projektu programu Visual Studio.
ms.date: 11/09/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6f7116ab5dc6c77f88d0787beac32d1c1e0a4716
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966571"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Projekt systemu Linux można skonfigurować tak, aby był przeznaczony dla maszyny zdalnej lub podsystemu Windows w systemie Linux (WSL). W przypadku maszyn zdalnych i WSL w programie Visual Studio 2017 należy skonfigurować połączenie zdalne.

## <a name="connect-to-a-remote-linux-computer"></a>Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux

Podczas kompilowania C++ projektu z systemem Linux dla zdalnego systemu Linux (maszyny wirtualnej lub maszyny fizycznej), kod źródłowy Linux jest kopiowany do zdalnego komputera z systemem Linux. Następnie jest kompilowany w oparciu o ustawienia programu Visual Studio.

Aby skonfigurować to połączenie zdalne:

1. Kompiluj projekt po raz pierwszy. Lub można utworzyć nowy wpis ręcznie. Wybierz pozycję **narzędzia > opcje**, Otwórz węzeł **Menedżer połączeń między platformami >** , a następnie wybierz przycisk **Dodaj** .

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W każdym scenariuszu zostanie wyświetlone okno **łączenie z systemem zdalnym** .

   ![Połącz z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Entry | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Przewożąc**                | Port, na którym działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Obsługiwane są zarówno hasło, jak i klucz prywatny
   | **Hasło**            | Hasło do podanej nazwy użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego został utworzony na potrzeby połączenia SSH
   | **Danym**          | Hasło użyte z wybranym powyżej kluczem prywatnym

   Do uwierzytelniania można użyć hasła lub pliku klucza i hasła. W przypadku wielu scenariuszy programistycznych uwierzytelnianie hasła jest wystarczające. Jeśli wolisz używać pliku klucza publicznego/prywatnego, możesz utworzyć nowy lub [ponownie użyć istniejącego](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Obecnie obsługiwane są tylko klucze RSA i DSA.

   Plik prywatnego klucza RSA można utworzyć, wykonując następujące czynności:

   1. Na komputerze z systemem Windows Utwórz parę kluczy SSH z `ssh-keygen -t rsa`. Polecenie tworzy klucz publiczny i klucz prywatny. Domyślnie klucze są umieszczane w obszarze `C:\Users\%USERNAME%\.ssh`przy użyciu nazw `id_rsa.pub` i `id_rsa`.

   1. W systemie Windows skopiuj klucz publiczny na komputer z systemem Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

   1. W systemie Linux Dodaj klucz do listy autoryzowanych kluczy (i upewnij się, że plik ma odpowiednie uprawnienia): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Wybierz przycisk **Połącz** , aby podjąć próbę nawiązania połączenia z komputerem zdalnym.

   Jeśli połączenie powiedzie się, program Visual Studio rozpocznie Konfigurowanie funkcji IntelliSense do używania zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wprowadzania, które należy zmienić, są opisane na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Jeśli używasz plików kluczy do uwierzytelniania, upewnij się, że serwer SSH maszyny docelowej jest uruchomiony i skonfigurowany prawidłowo.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Przejdź do pozycji **narzędzia > opcje > rejestrowania Międzyplatformowego >** , aby włączyć rejestrowanie w celu ułatwienia rozwiązywania problemów z połączeniami:

   ![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

   Dzienniki obejmują połączenia, wszystkie polecenia wysyłane do maszyny zdalnej (ich tekst, kod zakończenia i czas wykonywania) oraz wszystkie dane wyjściowe z programu Visual Studio do powłoki. Rejestrowanie działa w przypadku dowolnego projektu CMake na wielu platformach lub w programie Visual Studio opartym na programie MSBuild.

   Można skonfigurować dane wyjściowe, aby przejść do pliku lub okienka **rejestrowania między platformami** w okno dane wyjściowe. W przypadku projektów systemu Linux opartych na programie MSBuild polecenia programu MSBuild wysyłane do maszyny zdalnej nie są kierowane do **okno dane wyjściowe** , ponieważ są emitowane poza procesem. Zamiast tego są one rejestrowane w pliku z prefiksem "msbuild_".

## <a name="tcp-port-forwarding"></a>Przekazywanie portów TCP

Obsługa systemu Linux w programie Visual Studio ma zależność od przekazywania portów TCP. Jeśli przekazywanie portów TCP jest wyłączone w systemie zdalnym, wpłynie to na **rsync** i **serwera gdbserver** . 

rsync jest używany przez projekty systemu Linux oparte na programie MSBuild i projekty CMake do [kopiowania nagłówków z zdalnego komputera do systemu Windows do użycia przez funkcję IntelliSense](configure-a-linux-project.md#remote_intellisense). Gdy nie można włączyć przekazywania portów TCP, wyłącz automatyczne pobieranie nagłówków zdalnych. Aby go wyłączyć, użyj **narzędzi > opcje > Międzyplatformowe > Menedżer połączeń > zdalnych nagłówków IntelliSense**. Jeśli system zdalny nie ma włączonego przekazywania portów TCP, zobaczysz ten błąd, jeśli pobieranie zdalnych nagłówków dla funkcji IntelliSense rozpocznie się:

![Błąd nagłówków](media/port-forwarding-headers-error.png)

Rsync jest również używany przez wsparcie CMake programu Visual Studio do kopiowania plików źródłowych do systemu zdalnego. Jeśli nie możesz włączyć przekazywania portów TCP, możesz użyć protokołu SFTP jako metody źródła kopiowania zdalnego. protokół SFTP jest często wolniejszy niż rsync, ale nie ma zależności od przekazywania portów TCP. Metodami kopiowania zdalnego można zarządzać za pomocą właściwości **remoteCopySourcesMethod** w [Edytorze ustawień CMAKE](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Jeśli przekazywanie portów TCP jest wyłączone w systemie zdalnym, w oknie danych wyjściowych CMake zostanie wyświetlony komunikat o błędzie podczas pierwszego uruchomienia rsync.

![Błąd rsync](media/port-forwarding-copy-error.png)

Serwera gdbserver może służyć do debugowania na urządzeniach osadzonych. Jeśli nie możesz włączyć przekazywania portów TCP, musisz użyć GDB dla wszystkich scenariuszy zdalnego debugowania. GDB jest używana domyślnie podczas debugowania projektów w systemie zdalnym.

::: moniker-end

## <a name="connect-to-wsl"></a>Nawiązywanie połączenia z usługą WSL

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
