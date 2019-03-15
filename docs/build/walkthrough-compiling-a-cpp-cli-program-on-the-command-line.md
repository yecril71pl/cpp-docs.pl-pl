---
title: 'Przewodnik: Kompilowanie programu w języku C + +/ interfejsu wiersza polecenia programu w wierszu polecenia'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811930"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Przewodnik: Kompilowanie programu w języku C + +/ interfejsu wiersza polecenia programu w wierszu polecenia

Tworzenie programów Visual C++, które docelowe środowisko uruchomieniowe języka wspólnego (CLR) i używać programu .NET Framework i utworzyć je w wiersza polecenia. Visual C++ obsługuje C + +/ języka programowania interfejsu wiersza polecenia, który ma dodatkowe typy i operatory, pod kątem model programowania .NET. Ogólne informacje o języku C + +/ interfejsu wiersza polecenia języka, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

W tym przewodniku umożliwia edytora tekstu Utwórz podstawowe języka C + +/ interfejsu wiersza polecenia programu, a następnie skompilować go w wierszu polecenia. (Możesz użyć własnego C + +/ interfejsu wiersza polecenia programu zamiast wpisywać ten, który jest wyświetlany, lub można użyć w języku C + +/ CLI przykładowy kod z innego artykułu pomocy. Ta technika jest przydatna do tworzenia i testowania małych modułów, które mają bez elementów interfejsu użytkownika).

## <a name="prerequisites"></a>Wymagania wstępne

Należy zrozumieć podstawy języka C++.

## <a name="compiling-a-ccli-program"></a>Kompilowanie programu w języku C + +/ interfejsu wiersza polecenia programu

Poniższe kroki pokazują jak skompilować w języku C + +/ CLI aplikację konsolową, która używa klas .NET Framework.

Aby włączyć kompilacji w języku C + +/ CLI, należy użyć [/CLR](reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator MSVC generuje plik .exe, który zawiera kod MSIL — lub mieszanego MSIL i kodu natywnego — i linki do wymaganych bibliotek .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Aby skompilować w języku C + +/ interfejsu wiersza polecenia aplikacji w wierszu polecenia

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
[Projekty i systemów kompilacji](projects-and-build-systems-cpp.md)<br/>
[MSVC Compiler Options](reference/compiler-options.md)
