---
title: Konfigurowanie bezpiecznego tworzenia zdalnego systemu Linux zgodnego ze standardem FIPS
description: Jak skonfigurować połączenie kryptograficzne zgodne ze standardem FIPS między programem Visual Studio i maszyną z systemem Linux na potrzeby tworzenia zdalnego.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520894"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Konfigurowanie bezpiecznego tworzenia zdalnego systemu Linux zgodnego ze standardem FIPS

::: moniker range="<=vs-2017"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych. Bezpieczne programowanie zdalnego systemu Linux zgodne ze standardem FIPS jest dostępne w programie Visual Studio 2019 w wersji 16,5 lub nowszej.

::: moniker-end

::: moniker range="vs-2019"

Publikacja Federal Information Processing Standard (FIPS) 140-2 jest standardem dla modułów kryptograficznych dla instytucji rządowych USA. Implementacje standardu są weryfikowane przez instytut NIST. System Windows sprawdził [sprawdzoną obsługę modułów kryptograficznych zgodnych ze standardem FIPS](/windows/security/threat-protection/fips-140-validation). W programie Visual Studio 2019 w wersji 16,5 lub nowszej można użyć bezpiecznego, zgodnego ze standardem FIPS połączenia kryptograficznego z systemem Linux na potrzeby zdalnego tworzenia aplikacji.

Poniżej przedstawiono sposób konfigurowania bezpiecznego połączenia zgodnego ze standardem FIPS między programem Visual Studio i zdalnym systemem Linux. Ten przewodnik ma zastosowanie w przypadku kompilowania projektów CMake lub MSBuild Linux w programie Visual Studio. Ten artykuł zawiera informacje o wersji zgodnej ze standardem FIPS w temacie [łączenie ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Przygotuj połączenie zgodne ze standardem FIPS

Niektóre przygotowania są wymagane do używania zgodnego ze standardem FIPS połączenia SSH zabezpieczonego za pośrednictwem programu Visual Studio i zdalnego systemu Linux. W przypadku zgodności ze standardem FIPS-140-2 program Visual Studio obsługuje tylko klucze RSA.

W przykładach w tym artykule użyto Ubuntu 18,04 LTS z OpenSSH Server 7,6. Jednak instrukcje powinny być takie same dla każdego dystrybucjiu, w którym jest używana najnowsza wersja OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Aby skonfigurować serwer SSH w systemie zdalnym

1. W systemie Linux Zainstaluj i uruchom serwer OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Jeśli chcesz, aby serwer SSH był uruchamiany automatycznie podczas uruchamiania systemu, włącz go przy użyciu systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Otwórz *sshd_config/etc/ssh/* jako element główny. Edytuj (lub Dodaj, jeśli nie istnieje) następujące wiersze:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > SSH-RSA jest jedynym algorytmem klucza hosta zgodnym ze standardem FIPS a obsługiwanym przez program. Algorytmy AES\*-Rob są również zgodne ze standardem FIPS, ale implementacja w programie Visual Studio nie jest zatwierdzona. Algorytmy wymiany kluczy ECDH\* są zgodne ze standardem FIPS, ale nie są obsługiwane przez program Visual Studio.

   Te opcje nie są ograniczone. Protokół SSH można skonfigurować tak, aby korzystał z dodatkowych szyfrów, algorytmów kluczy hosta i tak dalej. Niektóre inne istotne opcje zabezpieczeń, które warto wziąć pod uwagę, to `PermitRootLogin`, `PasswordAuthentication`i `PermitEmptyPasswords`. Aby uzyskać więcej informacji, zapoznaj się ze stroną Man sshd_config lub z artykułu [Konfiguracja serwera SSH](https://www.ssh.com/ssh/sshd_config).

1. Po zapisaniu i zamknięciu sshd_config ponownie uruchom serwer SSH, aby zastosować nową konfigurację:

   ```bash
   sudo service ssh restart
   ```

Następnie utworzysz parę kluczy RSA na komputerze z systemem Windows. Następnie skopiujesz klucz publiczny do zdalnego systemu Linux do użycia przez protokół SSH.

### <a name="to-create-and-use-an-rsa-key-file"></a>Aby utworzyć plik klucza RSA i korzystać z niego

1. Na maszynie z systemem Windows Wygeneruj klucz publiczny/prywatny RSA z użyciem tego polecenia:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Polecenie tworzy klucz publiczny i klucz prywatny. Domyślnie klucze są zapisywane do *% USERPROFILE%\\. ssh\\id_rsa* i *% USERPROFILE%\\. SSH\\id_rsa. pub*. (W programie PowerShell Użyj `$env:USERPROFILE` zamiast makro cmd `%USERPROFILE%`) Jeśli zmienisz nazwę klucza, użyj zmienionej nazwy w kolejnych krokach.  Zalecamy korzystanie z hasła w celu zwiększenia bezpieczeństwa.

1. W systemie Windows skopiuj klucz publiczny na komputer z systemem Linux:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. W systemie Linux Dodaj klucz do listy autoryzowanych kluczy i upewnij się, że plik ma odpowiednie uprawnienia:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Teraz możesz sprawdzić, czy nowy klucz działa w SSH. Użyj go do logowania się z systemu Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Pomyślnie skonfigurowano protokół SSH, utworzono i wdrożono klucze szyfrowania i przetestowano połączenie. Teraz możesz przystąpić do skonfigurowania połączenia programu Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Nawiązywanie połączenia z systemem zdalnym w programie Visual Studio

1. W programie Visual Studio wybierz pozycję **narzędzia > opcje** na pasku menu, aby otworzyć okno dialogowe **Opcje** . Następnie wybierz pozycję **Międzyplatformowe > Menedżer połączeń** , aby otworzyć okno dialogowe Menedżera połączeń.

   Jeśli nie skonfigurowano połączenia w programie Visual Studio przed rozpoczęciem kompilowania projektu po raz pierwszy, program Visual Studio otwiera okno dialogowe Menedżera połączeń.

1. W oknie dialogowym Menedżer połączeń wybierz przycisk **Dodaj** , aby dodać nowe połączenie.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   Zostanie wyświetlone okno **łączenie z systemem zdalnym** .

   ![Połącz z systemem zdalnym](media/connect.png)

1. W oknie dialogowym **łączenie z systemem zdalnym** wprowadź szczegóły połączenia komputera zdalnego.

   | Entry | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, na którym działa usługa SSH, zazwyczaj 22
   | **Nazwa użytkownika**           | Użytkownik do uwierzytelniania jako
   | **Typ uwierzytelniania** | Wybieranie klucza prywatnego dla połączenia zgodnego ze standardem FIPS
   | **Plik klucza prywatnego**    | Plik klucza prywatnego został utworzony na potrzeby połączenia SSH
   | **Danym**          | Hasło użyte z wybranym powyżej kluczem prywatnym

   Zmień typ uwierzytelniania na **klucz prywatny**. Wprowadź ścieżkę do klucza prywatnego w polu **plik klucza prywatnego** . Możesz użyć przycisku **Przeglądaj** , aby przejść do pliku klucza prywatnego. Następnie wprowadź hasło używane do szyfrowania pliku klucza prywatnego w polu **hasło** .

1. Wybierz przycisk **Połącz** , aby podjąć próbę nawiązania połączenia z komputerem zdalnym.

   Jeśli połączenie powiedzie się, program Visual Studio skonfiguruje funkcję IntelliSense do używania zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wprowadzania, które należy zmienić, są opisane na czerwono.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   Aby uzyskać więcej informacji na temat rozwiązywania problemów z połączeniem, zobacz [nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Narzędzie wiersza polecenia dla Menedżera połączeń  

**Visual studio 2019 w wersji 16,5 lub nowszej**: ConnectionManager. exe to narzędzie wiersza polecenia do zarządzania połączeniami zdalnego tworzenia poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi nowej maszyny deweloperskiej. Można też użyć go do skonfigurowania programu Visual Studio na potrzeby ciągłej integracji. Przykłady i kompletne odwołanie do polecenia ConnectionManager można znaleźć w temacie [ConnectionManager Reference](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Opcjonalne: Włączanie lub wyłączanie trybu FIPS

W systemie Windows można włączyć tryb FIPS globalnie.

1. Aby włączyć tryb FIPS, naciśnij klawisze **Windows + R** , aby otworzyć okno dialogowe uruchamiania, a następnie uruchom gpedit. msc.

1. Rozwiń węzeł **zasady komputera lokalnego > Konfiguracja komputera > ustawienia systemu Windows > ustawienia zabezpieczeń > zasad lokalnych** i wybierz **Opcje zabezpieczeń**.

1. W obszarze **zasady**wybierz pozycję **Kryptografia systemu: Użyj zgodnych algorytmów FIPS do szyfrowania, mieszania i podpisywania**, a następnie naciśnij klawisz **Enter** , aby otworzyć okno dialogowe.

1. Na karcie **Ustawienia zabezpieczeń lokalnych** wybierz opcję **włączone** lub **wyłączone**, a następnie wybierz **przycisk OK** , aby zapisać zmiany.

> [!WARNING]
> Włączenie trybu FIPS może spowodować nieoczekiwane uszkodzenie lub zachowanie niektórych aplikacji. Aby uzyskać więcej informacji, zapoznaj się z wpisem w blogu [dlaczego nie zalecamy już używania trybu FIPS](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037).

## <a name="additional-resources"></a>Dodatkowe zasoby

[Dokumentacja firmy Microsoft dotycząca weryfikacji standardu FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: wymagania dotyczące zabezpieczeń dla modułów kryptograficznych](https://csrc.nist.gov/publications/detail/fips/140/2/final) (z NIST)

[Program weryfikacji algorytmu kryptograficznego: uwagi dotyczące walidacji](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (z NIST)

Wpis w blogu firmy Microsoft na tym, [dlaczego nie zalecamy już używania trybu FIPS](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Konfiguracja serwera SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Zobacz też

[Konfigurowanie\ projektu systemu Linux](configure-a-linux-project.md)
[Konfigurowanie\ projektu systemu Linux CMAKE](cmake-linux-project.md)
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](connect-to-your-remote-linux-computer.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurowanie sesji debugowania narzędzia CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
