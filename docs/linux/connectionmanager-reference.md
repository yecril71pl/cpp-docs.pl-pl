---
title: Odwołanie ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2b01bfbcd81984e7ddf32cd5ab0485fff17b3d2b
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520901"
---
# <a name="connectionmanager-reference"></a>Odwołanie ConnectionManager

::: moniker range="<=vs-2017"

ConnectionManager. exe jest dostępny w programie Visual Studio 2019 w wersji 16,5 lub nowszej.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager. exe to narzędzie wiersza polecenia do zarządzania połączeniami zdalnego tworzenia poza programem Visual Studio. Jest to przydatne w przypadku zadań, takich jak inicjowanie obsługi nowej maszyny deweloperskiej. Można też użyć go do skonfigurowania programu Visual Studio na potrzeby ciągłej integracji. Można go użyć w oknie wiersz polecenia dla deweloperów. Aby uzyskać więcej informacji na temat wiersz polecenia dla deweloperów, zobacz [Korzystanie z C++ zestawu narzędzi firmy Microsoft w wierszu polecenia](..\build\building-on-the-command-line.md).

ConnectionManager. exe jest dostępny w programie Visual Studio 2019 w wersji 16,5 lub nowszej. Jest to część rozwoju systemu **Linux z C++**  obciążeniem w Instalator programu Visual Studio. Jest ona również instalowana automatycznie po wybraniu składnika **Menedżera połączeń** w instalatorze. Jest on instalowany w systemie *% VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager. exe*.

Funkcja programu ConnectionManager. exe jest również dostępna w programie Visual Studio. Aby zarządzać połączeniami zdalnego tworzenia w środowisku IDE, na pasku menu wybierz polecenie **narzędzia** > **Opcje** , aby otworzyć okno dialogowe Opcje. W oknie dialogowym Opcje wybierz pozycję **Międzyplatformowe** > **Menedżer połączeń**.

## <a name="syntax"></a>Składnia

> **ConnectionManager. exe** *polecenie* \[*argumenty*] \[*Opcje*]

### <a name="commands-and-arguments"></a>Polecenia i argumenty

- **dodawanie** *\@użytkownika Host* \[ **--** *Port port]* \[ **--** Password *Password*] \[ **--PrivateKey** *privatekey_file*]

  Uwierzytelnia i dodaje nowe połączenie. Domyślnie używa on portu 22 i uwierzytelniania hasła. (Zostanie wyświetlony monit o wprowadzenie hasła). Aby określić hasło dla klucza prywatnego, użyj **hasła--Password** i **--PrivateKey** .

- **usuń** \[*connection_id* \| *użytkownika\@hosta* \[ **--port** *port*]]

  Usuwa połączenie. Jeśli nie określono żadnych argumentów, zostanie wyświetlony monit o określenie, które połączenie ma zostać usunięte.

- **Usuń wszystko**

  Usuwa wszystkie przechowywane połączenia.

- **list**

  Wyświetla informacje i identyfikatory wszystkich przechowywanych połączeń.

- **Pomoc**

  Wyświetla ekran pomoc.

- **version**

  Wyświetla informacje o wersji.

### <a name="options"></a>Opcje

- **-q**, **--quiet**

  Uniemożliwia wyjście do `stdout` lub `stderr`.

- **--No-Prompt**

  Niepowodzenie zamiast monitu, w razie potrzeby.

- **--No-verify**

  Dodaj lub zmodyfikuj połączenie bez uwierzytelniania.

- **--** *filename* pliku

  Odczytaj informacje o połączeniu z podanej *nazwy pliku*.

- **--No-Telemetria**

  Wyłącz wysyłanie danych użycia z powrotem do firmy Microsoft. Dane użycia są zbierane i wysyłane do firmy Microsoft, chyba że została przeniesiona flaga **--no-telemetrion** .  

- **-n**, **--osuszyć-Run**

  Wykonuje polecenie w postaci suchego przebiegu.

- **-p**

  Takie samo jak **hasło**.

- **-i**

  Analogicznie jak **--PrivateKey**.

## <a name="examples"></a>Przykłady

To polecenie dodaje połączenie dla użytkownika o nazwie "User" na hoście lokalnym. Połączenie używa pliku klucza do uwierzytelniania, który znajduje się w *% USERPROFILE%\.SSH \ id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

To polecenie usuwa połączenie z IDENTYFIKATORem 1975957870 z listy połączeń.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Zobacz także

[Nawiązywanie połączenia z docelowym systemem Linux w programie Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
