---
title: Konfigurowanie zgodnego ze standardem FIPS, bezpiecznego i zdalnego środowiska tworzenia dla systemu Linux
description: Jak skonfigurować połączenie kryptograficzne zgodne ze standardem FIPS między programem Visual Studio a komputerem z systemem Linux w celu zdalnego programowania.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520894"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Konfigurowanie zgodnego ze standardem FIPS, bezpiecznego i zdalnego środowiska tworzenia dla systemu Linux

::: moniker range="<=vs-2017"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych. Bezpieczne zdalne tworzenie systemu Linux zgodne ze standardem FIPS jest dostępne w programie Visual Studio 2019 w wersji 16.5 i nowszej.

::: moniker-end

::: moniker range="vs-2019"

Publikacja 140-2 federalnego standardu przetwarzania informacji (FIPS) jest standardem rządu STANÓW Zjednoczonych dla modułów kryptograficznych. Implementacje standardu są weryfikowane przez NIST. System Windows [potwierdził obsługę modułów kryptograficznych zgodnych ze standardem FIPS.](/windows/security/threat-protection/fips-140-validation) W programie Visual Studio 2019 w wersji 16.5 lub nowszej można użyć bezpiecznego połączenia kryptograficznego zgodnego ze standardem FIPS z systemem Linux w celu zdalnego rozwoju.

Poniżej opisano, jak skonfigurować bezpieczne połączenie zgodne ze standardem FIPS między programem Visual Studio a zdalnym systemem Linux. Ten przewodnik ma zastosowanie podczas tworzenia projektów CMake lub MSBuild Linux w programie Visual Studio. Ten artykuł jest zgodna ze standardem FIPS wersja instrukcji połączenia w [Połącz ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Przygotowanie połączenia zgodnego ze standardem FIPS

Niektóre przygotowanie jest wymagane do korzystania ze zgodnych z FIPS, kryptograficznie bezpieczne połączenie ssh między visual studio i zdalnego systemu Linux. W przypadku zgodności z fips-140-2 program Visual Studio obsługuje tylko klucze RSA.

Przykłady w tym artykule używają Ubuntu 18.04 LTS z serwerem OpenSSH w wersji 7.6. Jednak instrukcje powinny być takie same dla każdej dystrybucji przy użyciu umiarkowanie najnowszej wersji OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Aby skonfigurować serwer SSH w systemie zdalnym

1. W systemie Linux zainstaluj i uruchom serwer OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Jeśli chcesz, aby serwer ssh uruchamiał się automatycznie po uruchomieniu systemu, włącz go za pomocą systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Otwórz */etc/ssh/sshd_config* jako root. Edytuj (lub dodaj, jeśli nie istnieją) następujące wiersze:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa jest jedynym zgodnym z FIPS algorytmem klucza hosta vs obsługuje. Algorytmy\*aes -ctr są również zgodne z FIPS, ale implementacja w programie Visual Studio nie została zatwierdzona. Algorytmy wymiany\* kluczy ecdh są zgodne z FIPS, ale visual studio nie obsługuje ich.

   Nie ograniczasz się do tych opcji. Można skonfigurować ssh do używania dodatkowych szyfrów, algorytmów klucza hosta i tak dalej. Niektóre inne odpowiednie opcje zabezpieczeń, `PermitRootLogin`które `PasswordAuthentication`warto `PermitEmptyPasswords`rozważyć, to , i . Aby uzyskać więcej informacji, zobacz stronę man sshd_config lub artykuł [Konfiguracja serwera SSH](https://www.ssh.com/ssh/sshd_config).

1. Po zapisaniu i zamknięciu sshd_config uruchom ponownie serwer ssh, aby zastosować nową konfigurację:

   ```bash
   sudo service ssh restart
   ```

Następnie utworzysz parę kluczy RSA na komputerze z systemem Windows. Następnie skopiujesz klucz publiczny do zdalnego systemu Linux do użytku przez ssh.

### <a name="to-create-and-use-an-rsa-key-file"></a>Aby utworzyć i używać pliku klucza RSA

1. Na komputerze z systemem Windows wygeneruj publiczną/prywatną parę kluczy RSA za pomocą tego polecenia:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Polecenie tworzy klucz publiczny i klucz prywatny. Domyślnie klucze są zapisywane w *%USERPROFILE%\\.ssh\\id_rsa* i *%USERPROFILE%\\.ssh\\id_rsa.pub*. (W programie Powershell użyj `$env:USERPROFILE` zamiast makra `%USERPROFILE%`cmd) Jeśli zmienisz nazwę klucza, użyj zmienionej nazwy w kolejnych krokach.  Zalecamy użycie hasła w celu zwiększenia bezpieczeństwa.

1. Z systemu Windows skopiuj klucz publiczny na komputerze z systemem Linux:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. W systemie Linux dodaj klucz do listy autoryzowanych kluczy i upewnij się, że plik ma poprawne uprawnienia:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Teraz możesz sprawdzić, czy nowy klucz działa w ssh. Użyj go, aby zalogować się z systemu Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Pomyślnie skonfigurowano ssh, utworzono i wdrożono klucze szyfrowania oraz przetestowano połączenie. Teraz możesz przystąpić do konfigurowania połączenia programu Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Łączenie się z systemem zdalnym w programie Visual Studio

1. W programie Visual Studio wybierz pozycję **Narzędzia > opcje** na pasku menu, aby otworzyć okno dialogowe **Opcje.** Następnie wybierz **Międzyplatformowe > Menedżera połączeń,** aby otworzyć okno dialogowe Menedżera połączeń.

   Jeśli połączenie nie zostały wcześniej skonfigurowane w programie Visual Studio, podczas tworzenia projektu po raz pierwszy program Visual Studio otworzy okno dialogowe Menedżera połączeń.

1. W oknie dialogowym Menedżer połączeń wybierz przycisk **Dodaj,** aby dodać nowe połączenie.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   Zostanie wyświetlone okno **Połącz z systemem zdalnym.**

   ![Łączenie się z systemem zdalnym](media/connect.png)

1. W oknie dialogowym **Połącz z systemem zdalnym** wprowadź szczegóły połączenia komputera zdalnego.

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Portu**                | Port, na który działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Wybieranie klucza prywatnego dla połączenia zgodnego ze standardem FIPS
   | **Plik klucza prywatnego**    | Plik klucza prywatnego utworzony dla połączenia ssh
   | **Hasło**          | Hasło używane z wybranym kluczem prywatnym powyżej

   Zmień typ uwierzytelniania na **Klucz prywatny**. Wprowadź ścieżkę do klucza prywatnego w polu **Plik klucza prywatnego.** Za pomocą przycisku **Przeglądaj** można przejść do pliku klucza prywatnego. Następnie wprowadź hasło używane do szyfrowania pliku klucza prywatnego w polu **Hasło.**

1. Wybierz przycisk **Połącz,** aby spróbować nawiązać połączenie z komputerem zdalnym.

   Jeśli połączenie zakończy się pomyślnie, visual studio konfiguruje IntelliSense używać zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wejścia, które należy zmienić, są zaznaczone na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Aby uzyskać więcej informacji na temat rozwiązywania problemów z połączeniem, zobacz [Łączenie się ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Narzędzie wiersza polecenia dla Menedżera połączeń  

**Visual Studio 2019 w wersji 16.5 lub nowszej:** ConnectionManager.exe jest narzędziem wiersza polecenia do zarządzania połączeniami zdalnego programowania poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi administracyjnej nowego komputera dewelopera. Lub można go użyć do skonfigurowania programu Visual Studio do ciągłej integracji. Przykłady i pełne odwołanie do polecenia ConnectionManager można znaleźć w [1944 roku.](connectionmanager-reference.md)  

## <a name="optional-enable-or-disable-fips-mode"></a>Opcjonalnie: Włączanie lub wyłączanie trybu FIPS

Jest to możliwe, aby włączyć tryb FIPS globalnie w systemie Windows.

1. Aby włączyć tryb FIPS, naciśnij **klawisze Windows+R,** aby otworzyć okno dialogowe Uruchom, a następnie uruchom plik gpedit.msc.

1. Rozwiń pozycję **Konfiguracja komputera lokalnego > > ustawieniami zabezpieczeń systemu Windows > ustawieniami zabezpieczeń > zasady lokalne** i wybierz pozycję Opcje **zabezpieczeń**.

1. W obszarze **Zasady**wybierz **pozycję Kryptografia systemu: Użyj algorytmów zgodnych ze standardem FIPS do szyfrowania, mieszania i podpisywania,** a następnie naciśnij **klawisz Enter,** aby otworzyć jego okno dialogowe.

1. Na karcie **Lokalne ustawienie zabezpieczeń** wybierz pozycję **Włączone** lub **Wyłączone**, a następnie wybierz przycisk **OK,** aby zapisać zmiany.

> [!WARNING]
> Włączenie trybu FIPS może spowodować, że niektóre aplikacje się zepsują lub będą zachowywać się nieoczekiwanie. Aby uzyskać więcej informacji, zobacz wpis na blogu [Dlaczego już nie polecamy "trybu FIPS".](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

## <a name="additional-resources"></a>Zasoby dodatkowe

[Dokumentacja firmy Microsoft dotycząca sprawdzania poprawności FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: Wymagania dotyczące zabezpieczeń modułów kryptograficznych](https://csrc.nist.gov/publications/detail/fips/140/2/final) (od NIST)

[Program sprawdzania poprawności algorytmów kryptograficznych: uwagi dotyczące sprawdzania poprawności](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (z NIST)

Microsoft blogu dlaczego [nie polecamy "tryb FIPS" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Konfiguracja serwera SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Zobacz też

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)\
[Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)\
[Połącz się ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
