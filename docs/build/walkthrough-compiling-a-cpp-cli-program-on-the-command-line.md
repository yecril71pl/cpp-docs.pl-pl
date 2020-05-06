---
title: 'Wskazówki: kompilowanie programu w języku C++/CLI w wierszu polecenia'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877454"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Wskazówki: kompilowanie programu w języku C++/CLI w wierszu polecenia

Można utworzyć Visual C++ programów przeznaczonych dla środowiska uruchomieniowego języka wspólnego (CLR) i użyć .NET Framework i skompilować je w wierszu polecenia. Visual C++ obsługuje język programowania C++/CLI, który zawiera dodatkowe typy i operatory przeznaczone dla modelu programowania .NET. Aby uzyskać ogólne informacje na temat języka C++/CLI, zobacz [programowanie .NET przy użyciu języka c++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

W tym instruktażu należy użyć edytora tekstów do utworzenia podstawowego programu C++/CLI, a następnie skompilowania go w wierszu polecenia. (Możesz użyć własnego programu C++/CLI zamiast wpisywać ten, który jest wyświetlany, lub możesz użyć przykładowego kodu C++/CLI z innego artykułu pomocy. Ta technika jest przydatna do kompilowania i testowania małych modułów, które nie mają elementów interfejsu użytkownika.

## <a name="prerequisites"></a>Wymagania wstępne

Rozumiesz podstawy języka C++.

## <a name="compiling-a-ccli-program"></a>Kompilowanie programu w języku C++/CLI

Poniższe kroki pokazują, jak skompilować aplikację konsolową C++/CLI, która używa klas .NET Framework.

Aby włączyć kompilację dla/CLI C++, należy użyć opcji kompilatora [/CLR](reference/clr-common-language-runtime-compilation.md) . Kompilator MSVC generuje plik. exe, który zawiera kod MSIL — lub mieszany kod MSIL i natywny, oraz linki do wymaganych bibliotek .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Aby skompilować aplikację C++/CLI w wierszu polecenia

1. Otwórz okno **wiersz polecenia dla deweloperów** . Aby uzyskać szczegółowe instrukcje, zobacz, [Aby otworzyć okno wiersza polecenia dla deweloperów](building-on-the-command-line.md#developer_command_prompt).

   Do pomyślnego skompilowania kodu w zależności od systemu operacyjnego i konfiguracji komputera może być wymagane poświadczenie administratora. Aby uruchomić okno wiersza polecenia jako administrator, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla wiersza polecenia, a następnie wybierz polecenie **więcej** > **Uruchom jako administrator**.

1. W wierszu polecenia wpisz `notepad basicclr.cpp`polecenie.

   Wybierz opcję **tak** po wyświetleniu monitu o utworzenie pliku.

1. W Notatniku wprowadź następujące wiersze:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Na pasku menu wybierz **plik** > **Zapisz**.

   Utworzono plik źródłowy Visual C++, który używa klasy .NET Framework (<xref:System.Console>) w <xref:System> przestrzeni nazw.

1. W wierszu polecenia wpisz `cl /clr basicclr.cpp`polecenie. Kompilator CL. exe kompiluje kod źródłowy do pliku. obj, który zawiera MSIL, a następnie uruchamia konsolidator w celu wygenerowania programu wykonywalnego o nazwie basicclr. exe.

1. Aby uruchomić program basicclr. exe, w wierszu polecenia wpisz `basicclr`polecenie.

   Program wyświetla ten tekst i opuszcza:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
