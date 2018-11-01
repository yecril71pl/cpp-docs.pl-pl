---
title: 'Wskazówki: kompilowanie programu w języku C++/CLI w wierszu polecenia'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: e8841600fd61aacfe5b942ac4a4305619dff7e90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451028"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Wskazówki: kompilowanie programu w języku C++/CLI w wierszu polecenia

Tworzenie programów Visual C++, które docelowe środowisko uruchomieniowe języka wspólnego (CLR) i używać programu .NET Framework i utworzyć je w wiersza polecenia. Visual C++ obsługuje C + +/ języka programowania interfejsu wiersza polecenia, który ma dodatkowe typy i operatory, pod kątem model programowania .NET. Ogólne informacje o języku C + +/ interfejsu wiersza polecenia języka, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

W tym przewodniku umożliwia edytora tekstu Utwórz podstawowe języka C + +/ interfejsu wiersza polecenia programu, a następnie skompilować go w wierszu polecenia. (Możesz użyć własnego C + +/ interfejsu wiersza polecenia programu zamiast wpisywać ten, który jest wyświetlany, lub można użyć w języku C + +/ CLI przykładowy kod z innego artykułu pomocy. Ta technika jest przydatna do tworzenia i testowania małych modułów, które mają bez elementów interfejsu użytkownika).

> [!NOTE]
> Umożliwia także środowiska IDE programu Visual Studio do kompilowania C + +/ interfejsu wiersza polecenia programów. Aby uzyskać więcej informacji, zobacz [wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w programie Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).

## <a name="prerequisites"></a>Wymagania wstępne

Należy zrozumieć podstawy języka C++.

## <a name="compiling-a-ccli-program"></a>Kompilowanie programu w języku C + +/ interfejsu wiersza polecenia programu

Poniższe kroki pokazują jak skompilować w języku C + +/ CLI aplikację konsolową, która używa klas .NET Framework.

Aby włączyć kompilacji w języku C + +/ CLI, należy użyć [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator Visual C++ generuje plik .exe, który zawiera kod MSIL — lub mieszanego MSIL i kodu natywnego — i linki do wymaganych bibliotek .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Aby skompilować w języku C + +/ interfejsu wiersza polecenia aplikacji w wierszu polecenia

1. Otwórz **wiersz polecenia dla deweloperów** okna. Aby uzyskać szczegółowe instrukcje, zobacz [aby otworzyć okno wiersza polecenia dewelopera](../build/building-on-the-command-line.md#developer_command_prompt).

   Poświadczenia administratora może być konieczne pomyślnie skompilować kod, w zależności od konfiguracji i systemu operacyjnego komputera. Aby uruchomić okno wiersza polecenia jako administrator, kliknij prawym przyciskiem myszy Otwórz menu skrótów dla wiersza polecenia, a następnie wybierz polecenie **więcej** > **Uruchom jako administrator**.

1. W wierszu polecenia wprowadź `notepad basicclr.cpp`.

   Wybierz **tak** po wyświetleniu monitu, czy można utworzyć pliku.

1. W programie Notatnik wprowadź następujące wiersze:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Na pasku menu wybierz **pliku** > **Zapisz**.

   Utworzono plik źródłowy języka Visual C++, który używa klasy .NET Framework (<xref:System.Console>) w <xref:System> przestrzeni nazw.

1. W wierszu polecenia wprowadź `cl /clr basicclr.cpp`. Cl.exe — kompilator kompiluje kod źródłowy w pliku .obj, który zawiera MSIL, a następnie uruchamia konsolidator generuje program wykonywalny o nazwie basicclr.exe.

1. Aby uruchomić basicclr.exe program w wierszu polecenia, wprowadź `basicclr`.

   Ten program wyświetla ten tekst i kończy działanie:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br/>
[Opcje kompilatora](../build/reference/compiler-options.md)
