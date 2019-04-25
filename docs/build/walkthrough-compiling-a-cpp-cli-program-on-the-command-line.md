---
title: 'Przewodnik: Kompilowanie C++Program w sposób niezamierzony w wierszu polecenia'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314172"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Przewodnik: Kompilowanie C++Program w sposób niezamierzony w wierszu polecenia

Tworzenie programów Visual C++, które docelowe środowisko uruchomieniowe języka wspólnego (CLR) i używać programu .NET Framework i utworzyć je w wiersza polecenia. Wizualne C++ obsługuje C++/CLI, język programowania, który ma dodatkowe typy i operatory, pod kątem model programowania .NET. Aby uzyskać ogólne informacje o C++języka w sposób niezamierzony, zobacz [.NET, programowanie za pomocą C++sposób niezamierzony (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

W tym przewodniku, użyj edytora tekstu do utworzenia podstawowego C++sposób niezamierzony program, a następnie skompilować go w wierszu polecenia. (Można użyć własnych C++/programu interfejsu wiersza polecenia zamiast wpisywać taki, który jest wyświetlany, lub użyć C++przykładowy kod w sposób niezamierzony z innego artykułu pomocy. Ta technika jest przydatna do tworzenia i testowania małych modułów, które mają bez elementów interfejsu użytkownika).

## <a name="prerequisites"></a>Wymagania wstępne

Należy zrozumieć podstawy języka C++.

## <a name="compiling-a-ccli-program"></a>Kompilowanie C++Program w sposób niezamierzony

Poniższe kroki pokazują jak skompilować C++sposób niezamierzony aplikację konsolową, która używa klas .NET Framework.

Aby włączyć kompilowanie C++/interfejsu wiersza polecenia, należy użyć [/CLR](reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator MSVC generuje plik .exe, który zawiera kod MSIL — lub mieszanego MSIL i kodu natywnego — i linki do wymaganych bibliotek .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Aby skompilować C++aplikacji w sposób niezamierzony w wierszu polecenia

1. Otwórz **wiersz polecenia dla deweloperów** okna. Aby uzyskać szczegółowe instrukcje, zobacz [aby otworzyć okno wiersza polecenia dewelopera](building-on-the-command-line.md#developer_command_prompt).

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
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
