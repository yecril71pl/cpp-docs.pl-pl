---
title: Łączenie do lokalizacji docelowej systemu Linux w programie Visual Studio
description: Nawiązywanie zdalnego maszyny z systemem Linux lub WSL w programie Visual Studio C++ projektu.
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 7fa09c49df3da39084edb6735a7a2ccc724c34d3
ms.sourcegitcommit: 3ae8025df7fd50f5f56a0a2b5396533218bcc7dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67285257"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Łączenie do lokalizacji docelowej systemu Linux w programie Visual Studio

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Można skonfigurować projektu systemu Linux pod kątem odległe albo podsystemu Windows dla systemu Linux (WSL). Komputerach zdalnych, a WSL programu Visual Studio 2017 musisz skonfigurować połączenie. 

## <a name="connect-to-a-remote-linux-computer"></a>Nawiązywanie zdalnego komputera z systemem Linux

Podczas kompilowania C++ projektu systemu Linux dla systemu Linux systemu zdalnego (maszyny Wirtualnej lub komputera fizycznego), Linux, kod jest kopiowany do komputera zdalnego systemu Linux, a następnie kompilowane zgodnie z ustawieniami programu Visual Studio.

Aby skonfigurować tego połączenia zdalnego:

1. Skompiluj projekt po raz pierwszy, albo ręcznie utworzyć nowy wpis, wybierając **Narzędzia > Opcje** , a następnie otwórz **wiele Platform > Menedżer połączeń** węzła i kliknij przycisk **Dodaj** przycisku.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W dowolnym scenariuszu **nawiązywanie połączenia z systemem zdalnym** zostanie wyświetlone okno.

   ![Łączenie z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, czy usługa SSH jest uruchomiona na ogół 22
   | **Nazwa użytkownika**           | Użytkownika do uwierzytelnienia się jako
   | **Typ uwierzytelniania** | Hasło lub klucz prywatny są obsługiwane
   | **Hasło**            | Hasło dla wprowadzona nazwa użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego dla protokołu ssh połączenie utworzone
   | **Hasło**          | Hasło używane razem z kluczem prywatnym w wybranym powyżej

   Można użyć hasła lub klucza pliku i hasło do uwierzytelniania. Umożliwia obsługę wielu scenariuszy programowania uwierzytelnianie za pomocą hasła jest wystarczająca. Jeśli wolisz używać pliku klucza publicznego i prywatnego, można utworzyć nową lub [ponowne użycie istniejącej](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Obecnie tylko klucze RSA i DSA są obsługiwane. 
   
   Można utworzyć plik klucza prywatnego RSA, wykonując następujące czynności:

    1. Na komputerze Windows utwórz klucz ssh twórz pary za pomocą `ssh-keygen -t rsa`. Spowoduje to utworzenie klucz publiczny i klucz prywatny. Domyślnie klucze są umieszczane w obszarze `C:\Users\%USERNAME%\.ssh` z nazwami `id_rsa.pub` i `id_rsa`.

    1. Windows, skopiuj klucz publiczny do maszyny z systemem Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. W systemie Linux Dodaj klucz do listy autoryzowanych kluczy (i upewnij się, że plik ma odpowiednie uprawnienia): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Kliknij przycisk **Connect** przycisk prób połączenia z komputerem zdalnym. 

   Jeśli połączenie powiedzie się, program Visual Studio rozpocznie się konfigurowanie funkcji IntelliSense, aby użyć zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wpisu, które muszą zostać zmienione zostały opisane w kolorze czerwonym.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Jeśli używane są pliki klucza uwierzytelniania, upewnij się, że serwer SSH na komputerze docelowym jest uruchomione i skonfigurowane prawidłowo.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Przejdź do **Narzędzia > Opcje > wiele Platform > Rejestrowanie** Aby włączyć rejestrowanie ułatwić rozwiązywanie problemów z połączeniem:

   ![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

   Dzienniki zawierają połączeń, wszystkie polecenia wysyłane do maszyny zdalnej (ich tekst, kod zakończenia i czasu wykonywania), a wszystkie dane wyjściowe z programu Visual Studio do powłoki. Rejestrowanie działania dla dowolnej projektu narzędzia CMake dla wielu platform opartych na platformie MSBuild projektu systemu Linux w programie Visual Studio.

   Możesz skonfigurować dane wyjściowe, aby przejść do pliku lub do **Cross Platform rejestrowania** okienka w oknie danych wyjściowych. W przypadku projektów opartych na platformie MSBuild Linux poleceń wysłanych do maszyny zdalnej przez program MSBuild nie są kierowane do **okno danych wyjściowych** ponieważ są one emitowany poza procesem. Zamiast tego są rejestrowane w pliku z prefiksem "msbuild_".

   ::: moniker-end

## <a name="connect-to-wsl"></a>Nawiązać połączenie z WSL

::: moniker range="vs-2017"

W programie Visual Studio 2017 możesz nawiązać WSL za pomocą tej samej procedury jak nawiązywanie zdalnego maszyny z systemem Linux, zgodnie z opisem we wcześniejszej części tego artykułu. Użyj **localhost** dla **nazwy hosta**.

::: moniker-end

::: moniker range="vs-2019"

W Visual Studio 2019 r wersji 16.1 nie jest konieczne do dodania połączenia zdalnego, lub skonfiguruj protokół SSH, jeśli WSL. To wszystko, co jest wymagane w systemie Linux, gcc, gdb, markę, rsync i zip. Program Visual Studio wymaga rsync i zip tylko do wyodrębnienia plików nagłówkowych przy pierwszym użyciu z wystąpienia WSL w systemie Windows plików używanych przez IntelliSense. W programie Visual Studio 2019 r wersji 16.1 Podpora WSL jest oparty na Windows wersja 1809. Może być uruchomiony nowszej wersji systemu Windows, ale Visual Studio nie jeszcze można skorzystać z nowych możliwości WSL.

Jeśli Twoja dystrybucji obsługuje apt, można zainstalować wymagane pakiety przy użyciu następującego polecenia:

```bash
sudo apt install g++ gdb make rsync zip
```

Aby skonfigurować projekt do WSL, zobacz [Konfigurowanie projektu systemu Linux](configure-a-linux-project.md) lub [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md) zależności od tego, jakiego rodzaju projektu masz.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)<br />
[Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)<br />
[Deply, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)<br />




