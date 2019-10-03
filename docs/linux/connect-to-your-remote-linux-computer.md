---
title: Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio
description: Jak nawiązać połączenie ze zdalną maszyną z systemem Linux lub WSL z C++ poziomu projektu programu Visual Studio.
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 2f4e6311493f2b29ba6911ec1b76225b6c7abe6d
ms.sourcegitcommit: b85e1db6b7d4919852ac6843a086ba311ae97d40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71925558"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Projekt systemu Linux można skonfigurować tak, aby był przeznaczony dla maszyny zdalnej lub podsystemu Windows w systemie Linux (WSL). W przypadku maszyn zdalnych i WSL w programie Visual Studio 2017 należy skonfigurować połączenie zdalne. 

## <a name="connect-to-a-remote-linux-computer"></a>Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux

Podczas kompilowania C++ projektu z systemem Linux dla zdalnego systemu Linux (maszyna wirtualna lub maszyna fizyczna), kod źródłowy Linux jest kopiowany do zdalnego komputera z systemem Linux, a następnie kompilowany na podstawie ustawień programu Visual Studio.

Aby skonfigurować to połączenie zdalne:

1. Kompiluj projekt po raz pierwszy lub ręcznie Utwórz nowy wpis, wybierając pozycję **narzędzia > opcje** , a następnie otwórz węzeł **Menedżer połączeń między platformami >** , a następnie kliknij przycisk **Dodaj** .

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W każdym scenariuszu zostanie wyświetlone okno **łączenie z systemem zdalnym** .

   ![Połącz z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, na którym działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Obsługiwane są zarówno hasło, jak i klucz prywatny
   | **Hasło**            | Hasło do podanej nazwy użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego został utworzony na potrzeby połączenia SSH
   | **Danym**          | Hasło użyte z wybranym powyżej kluczem prywatnym

   Do uwierzytelnienia można użyć hasła lub pliku klucza i hasła. W przypadku wielu scenariuszy programistycznych uwierzytelnianie hasła jest wystarczające. Jeśli wolisz używać pliku klucza publicznego/prywatnego, możesz utworzyć nowy lub [ponownie użyć istniejącego](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Obecnie obsługiwane są tylko klucze RSA i DSA. 
   
   Plik prywatnego klucza RSA można utworzyć, wykonując następujące czynności:

    1. Na komputerze z systemem Windows Utwórz parę kluczy SSH z `ssh-keygen -t rsa`. Spowoduje to utworzenie klucza publicznego i klucza prywatnego. Domyślnie klucze są umieszczane w obszarze `C:\Users\%USERNAME%\.ssh` z nazwami `id_rsa.pub` i `id_rsa`.

    1. W systemie Windows skopiuj klucz publiczny na komputer z systemem Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. W systemie Linux Dodaj klucz do listy autoryzowanych kluczy (i upewnij się, że plik ma odpowiednie uprawnienia): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Kliknij przycisk **Połącz** , aby podjąć próbę nawiązania połączenia z komputerem zdalnym. 

   Jeśli połączenie powiedzie się, program Visual Studio rozpocznie Konfigurowanie funkcji IntelliSense do używania zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wprowadzania, które należy zmienić, są opisane na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Jeśli używasz plików kluczy do uwierzytelniania, upewnij się, że serwer SSH maszyny docelowej jest uruchomiony i skonfigurowany prawidłowo.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Przejdź do pozycji **narzędzia > opcje > rejestrowania Międzyplatformowego >** , aby włączyć rejestrowanie w celu ułatwienia rozwiązywania problemów z połączeniami:

   ![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

   Dzienniki obejmują połączenia, wszystkie polecenia wysyłane do maszyny zdalnej (ich tekst, kod zakończenia i czas wykonywania) oraz wszystkie dane wyjściowe z programu Visual Studio do powłoki. Rejestrowanie działa w przypadku dowolnego projektu CMake na wielu platformach lub w programie Visual Studio opartym na programie MSBuild.

   Można skonfigurować dane wyjściowe, aby przejść do pliku lub okienka **rejestrowania między platformami** w okno dane wyjściowe. W przypadku projektów systemu Linux opartych na programie MSBuild polecenia wydane dla komputera zdalnego przez program MSBuild nie są kierowane do **okno dane wyjściowe** , ponieważ są emitowane poza procesem. Zamiast tego są one rejestrowane w pliku z prefiksem "msbuild_".

   ::: moniker-end

## <a name="connect-to-wsl"></a>Nawiązywanie połączenia z usługą WSL

::: moniker range="vs-2017"

W programie Visual Studio 2017 można nawiązać połączenie z usługą WSL, wykonując te same czynności co w przypadku nawiązywania połączenia ze zdalnym komputerem z systemem Linux zgodnie z opisem we wcześniejszej części tego artykułu. Użyj **nazwy hosta** **localhost** .

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 w wersji 16,1 dodano natywną C++ obsługę programu z [podsystemem Windows dla systemu Linux (WSL)](https://docs.microsoft.com/windows/wsl/about).  Oznacza to, że nie trzeba już dodawać połączenia zdalnego ani konfigurować protokołu SSH w celu kompilowania i debugowania lokalnej instalacji WSL. Szczegółowe informacje na [temat sposobu instalowania WSL](https://docs.microsoft.com/windows/wsl/install-win10) można znaleźć tutaj.

Aby skonfigurować instalację WSL do pracy z programem Visual Studio, potrzebne są następujące narzędzia: w zatoce lub Clang, GDB, marka, rsync i zip. Można je zainstalować na dystrybucje, które używają apt przy użyciu tego polecenia, które również instaluje kompilator g + +: 

```bash
sudo apt install g++ gdb make rsync zip
```
Aby uzyskać więcej informacji, zobacz [pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

Aby skonfigurować projekt dla programu WSL, zobacz [Konfigurowanie projektu systemu Linux](configure-a-linux-project.md) lub [Konfigurowanie projektu systemu Linux CMAKE](cmake-linux-project.md) w zależności od rodzaju projektu. Aby wykonać instrukcje krok po kroku dotyczące tworzenia prostej aplikacji konsolowej z WSL, zapoznaj się z tym wpisem na blogu wprowadzającym w [ C++ programie Visual Studio 2019 i podsystemem Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)<br />
[Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)<br />
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br />
[Konfigurowanie sesji debugowania CMake](../build/configure-cmake-debugging-sessions.md)
