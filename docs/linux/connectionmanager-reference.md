---
title: ConnectionManager — dokumentacja
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258036"
---
# <a name="connectionmanager-reference"></a>ConnectionManager — dokumentacja

::: moniker range="<=vs-2017"

Program ConnectionManager.exe jest dostępny w programie Visual Studio 2019 w wersji 16.5 i nowszej.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe to narzędzie wiersza polecenia do zarządzania zdalnymi połączeniami programistycznymi poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi administracyjnej nowego komputera dewelopera. Lub użyj go do skonfigurowania programu Visual Studio do ciągłej integracji.Można go używać w oknie wiersza polecenia dewelopera. Aby uzyskać więcej informacji na temat wiersza polecenia dewelopera, zobacz [Używanie zestawu narzędzi Microsoft C++ z wiersza polecenia](../build/building-on-the-command-line.md).

Program ConnectionManager.exe jest dostępny w programie Visual Studio 2019 w wersji 16.5 i nowszej. Jest częścią rozwoju **systemu Linux z c++** obciążenia w Instalatorze programu Visual Studio. Jest również instalowany automatycznie po wybraniu **składnika Menedżera połączeń** w instalatorze. Jest zainstalowany w *pliku ConnectionManager.exe\\\\w pliku %VCIDEInstallDir%\\Linux bin ConnectionManagerExe\\ConnectionManager.exe*.

Funkcjonalność programu ConnectionManager.exe jest również dostępna w programie Visual Studio. Aby zarządzać zdalnymi połączeniami programistycznymi w ide, na pasku menu wybierz pozycję**Opcje** **narzędzi,** > aby otworzyć okno dialogowe Opcje. W oknie dialogowym Opcje wybierz pozycję Menedżer połączeń **między platformami** > **Connection Manager**.

## <a name="syntax"></a>Składnia

> **ConnectionManager.exe** *argumenty* \[ *polecenia* \[] *opcje*]

### <a name="commands-and-arguments"></a>Polecenia i argumenty

- **dodaj** *\@hosta* \[użytkownika **--port** *portu*] \[ **--hasło** *hasło*] \[ **--privatekey** *privatekey_file*]

  Uwierzytelnia i dodaje nowe połączenie. Domyślnie używa uwierzytelniania portów 22 i hasła. (Zostanie wyświetlony monit o wprowadzenie hasła). Użyj hasła do klucza prywatnego za **pomocą funkcji --password** i **--privatekey.**

- **usuń** \[ *connection_id* \| *hosta\@* \[użytkownika **--port** *]]*

  Usuwa połączenie. Jeśli nie określono żadnych argumentów, zostanie wyświetlony monit o określenie, które połączenie należy usunąć.

- **usuń wszystko**

  Usuwa wszystkie zapisane połączenia.

- **list**

  Wyświetla informacje i identyfikatory wszystkich przechowywanych połączeń.

- **Pomoc**

  Wyświetla ekran pomocy.

- **Wersja**

  Wyświetla informacje o wersji.

### <a name="options"></a>Opcje

- **-q**, **--cichy**

  Zapobiega wyjściu `stdout` `stderr`do lub .

- **--no-prompt**

  Nie powiedzie się zamiast monitu, jeśli jest to konieczne.

- **--no-verify**

  Dodawanie lub modyfikowanie połączenia bez uwierzytelniania.

- **--nazwa** *pliku*

  Odczytu informacji o połączeniu z podanej *nazwy pliku*.

- **--no-telemetria**

  Wyłącz wysyłanie danych użycia z powrotem do firmy Microsoft. Dane użycia są zbierane i wysyłane z powrotem do firmy Microsoft, chyba że flaga **--no-telemetry** jest przekazywana.  

- **-n**, **--dry-run**

  Wykonuje suchy przebieg polecenia.

- **-p**

  Tak samo jak **--password**.

- **-i**

  Tak samo jak **--privatekey**.

## <a name="examples"></a>Przykłady

To polecenie dodaje połączenie dla użytkownika o nazwie "użytkownik" na localhost. Połączenie używa pliku klucza do uwierzytelniania, znajdującego się w *pliku %USERPROFILE%\.ssh\id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

To polecenie usuwa połączenie o identyfikatorze 1975957870 z listy połączeń.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Zobacz też

[Łączenie się z docelowym systemem Linux w programie Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
