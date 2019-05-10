---
title: 'Przewodnik: Kompilowanie C++Program /CX w wierszu polecenia'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: cbf5a48de3c029e36fc6daabe2b3f0db55dc173c
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877163"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Przewodnik: Kompilowanie C++Program /CX w wierszu polecenia

> [!NOTE] 
> Nowe aplikacje platformy uniwersalnej systemu Windows i składników, zaleca się użycie [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), standard C ++ 17 języka rzutowanie dla interfejsów API środowiska wykonawczego Windows. C++/ WinRT jest dostępna w Windows 10 SDK z wersji 1803 wartości. C++/ WinRT jest zaimplementowana w całości w plikach nagłówkowych i jest przeznaczony do zapewnia najwyższej jakości dostęp do nowoczesnego interfejsu Windows API.

Microsoft C++ kompilator (MSVC) obsługuje C++ rozszerzenia składnika (C++/CX), który ma dodatkowe typy i podmioty, pod kątem modelu programowania środowiska wykonawczego Windows. Możesz użyć C++/CX do tworzenia aplikacji uniwersalnych platformy Windows (UWP) i Windows desktop. Aby uzyskać więcej informacji, zobacz [Przewodnik po przykładzie C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) i [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

W tym przewodniku, użyj edytora tekstu do utworzenia podstawowego C++/CX programu, a następnie skompilować go w wierszu polecenia. (Można użyć własnych C++program /CX zamiast wpisywać ten, który jest wyświetlany, lub użyć C++/CX przykładowy kod z innego artykułu pomocy. Ta technika jest przydatna do tworzenia i testowania małych modułów, które mają bez elementów interfejsu użytkownika).

> [!NOTE]
> Umożliwia także środowiska IDE programu Visual Studio do kompilowania C++/CX programów. IDE zawiera projekt, debugowanie, emulacji i obsługa wdrażania, które nie są dostępne w wierszu polecenia, zaleca się używanie IDE do tworzenia aplikacji uniwersalnych platformy Windows (UWP). Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji platformy uniwersalnej systemu Windows w języku C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Wymagania wstępne

Należy zrozumieć podstawy języka C++.

## <a name="compiling-a-ccx-program"></a>Kompilowanie C++/CX programu

Aby włączyć kompilowanie C++/CX, należy użyć [/ZW](reference/zw-windows-runtime-compilation.md) — opcja kompilatora. Kompilator MSVC generuje plik .exe, który jest przeznaczony dla środowiska wykonawczego Windows, opinii i linkami do wymaganych bibliotek.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Aby skompilować C++/CX aplikacji w wierszu polecenia

1. Otwórz **wiersz polecenia dla deweloperów** okna. (Na **Start** otwarte okno **aplikacji**. Otwórz **Visual Studio Tools** folder w używanej wersji programu Visual Studio, a następnie wybierz **wiersz polecenia dla deweloperów** skrótów.) Aby uzyskać więcej informacji na temat otworzyć okno wiersza polecenia dla deweloperów, zobacz [możesz używać zestawu narzędzi MSVC z wiersza polecenia](building-on-the-command-line.md).

   Poświadczenia administratora może być konieczne pomyślnie skompilować kod, w zależności od konfiguracji i systemu operacyjnego komputera. Aby uruchomić okno wiersza polecenia jako administrator, otwórz menu skrótów dla **wiersz polecenia dla deweloperów** , a następnie wybierz **Uruchom jako administrator**.

1. W wierszu polecenia wprowadź **basiccx.cpp Notatnik**.

   Wybierz **tak** po wyświetleniu monitu, czy można utworzyć pliku.

1. W programie Notatnik wprowadź następujące wiersze:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Na pasku menu wybierz **pliku** > **Zapisz**.

   Utworzono C++ pliku źródłowego, który używa środowiska wykonawczego Windows [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md) przestrzeni nazw.

1. W wierszu polecenia wprowadź **cl/ehsc basiccx.cpp /ZW/Link opcji**. Cl.exe — kompilator kompiluje kod źródłowy w pliku .obj, a następnie uruchamia konsolidator generuje program wykonywalny o nazwie basiccx.exe. ( [/Ehsc](reference/eh-exception-handling-model.md) — opcja kompilatora Określa model obsługi wyjątków C++ i [/link](reference/link-pass-options-to-linker.md) Flaga Określa, aplikacja konsolowa.)

1. Aby uruchomić basiccx.exe program w wierszu polecenia, wprowadź **basiccx**.

   Ten program wyświetla ten tekst i kończy działanie:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
