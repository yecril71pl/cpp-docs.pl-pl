---
title: Łączenie do lokalizacji docelowej systemu Linux w programie Visual Studio
description: Nawiązywanie zdalnego maszyny z systemem Linux lub WSL w programie Visual Studio C++ projektu.
ms.date: 06/11/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 4003a7387981b60d22f0344463d1729974d437a7
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042680"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Łączenie do lokalizacji docelowej systemu Linux w programie Visual Studio

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Możesz skonfigurować projektu systemu Linux do docelowego komputera zdalnego lub podsystemu Windows dla systemu Linux (WSL).

## <a name="connect-to-a-remote-linux-computer"></a>Nawiązywanie zdalnego komputera z systemem Linux

Podczas kompilowania C++ projektu systemu Linux dla systemu Linux systemu zdalnego (maszyny Wirtualnej lub komputera fizycznego), Linux, kod jest kopiowany do komputera zdalnego systemu Linux, a następnie kompilowane zgodnie z ustawieniami programu Visual Studio. (W programie Visual Studio 2017, użyj tych instrukcji nawiązać WSL również. Użyj **localhost** dla **nazwy hosta**.)

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

1. Kliknij przycisk **Connect** przycisk prób połączenia z komputerem zdalnym. 

   Jeśli połączenie powiedzie się, program Visual Studio rozpocznie się konfigurowanie funkcji IntelliSense, aby użyć zdalnych nagłówków. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla nagłówków w systemach zdalnych](configure-a-linux-project.md#remote_intellisense).

   Jeśli połączenie nie powiedzie się, pola wpisu, które muszą zostać zmienione zostaną opisane w kolorze czerwonym.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   Przejdź do **Narzędzia > Opcje > wiele Platform > Rejestrowanie** Aby włączyć rejestrowanie ułatwić rozwiązywanie problemów z połączeniem:

   ![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

   Dzienniki zawierają połączeń, wszystkie polecenia wysyłane do maszyny zdalnej (ich tekst, kod zakończenia i czasu wykonywania), a wszystkie operacje zapisu w programie Visual Studio do powłoki. Rejestrowanie działania dla dowolnej projektu narzędzia CMake dla wielu platform opartych na platformie MSBuild projektu systemu Linux w programie Visual Studio.

   Możesz skonfigurować dane wyjściowe, aby przejść do pliku lub do **Cross Platform rejestrowania** okienka w oknie danych wyjściowych. W przypadku projektów opartych na platformie MSBuild Linux poleceń wysłanych do maszyny zdalnej przez program MSBuild nie są kierowane do **okno danych wyjściowych** ponieważ są one emitowany poza procesem. Zamiast tego są rejestrowane w pliku z prefiksem "msbuild_".

## <a name="connect-to-wsl"></a>Nawiązać połączenie z WSL

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




