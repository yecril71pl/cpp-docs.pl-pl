---
title: 'Przewodnik: Kompilowanie C++Program /CX w wierszu polecenia'
ms.date: 09/24/2018
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 099bef402d22abc12a31f105f63e5405c65a1d82
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766069"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Przewodnik: Kompilowanie C++Program /CX w wierszu polecenia

Można tworzyć programy Visual C++, które przeznaczone dla środowiska uruchomieniowego Windows i utworzyć je w wiersza polecenia. Wizualne C++ obsługuje Visual C++ rozszerzenia składnika (C++/CX), który ma dodatkowe typy i podmioty, pod kątem modelu programowania środowiska wykonawczego Windows. Możesz użyć C++/CX, aby tworzyć aplikacje dla Windows platformy Uniwersalnej systemu Windows Phone 8.1 i Windows desktop. Aby uzyskać więcej informacji, zobacz [Przewodnik po przykładzie C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) i [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

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

   Utworzono plik źródłowy języka Visual C++, który używa środowiska wykonawczego Windows [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md) przestrzeni nazw.

1. W wierszu polecenia wprowadź **cl/ehsc basiccx.cpp /ZW/Link opcji**. Cl.exe — kompilator kompiluje kod źródłowy w pliku .obj, a następnie uruchamia konsolidator generuje program wykonywalny o nazwie basiccx.exe. ( [/Ehsc](reference/eh-exception-handling-model.md) — opcja kompilatora Określa model obsługi wyjątków C++ i [/link](reference/link-pass-options-to-linker.md) Flaga Określa, aplikacja konsolowa.)

1. Aby uruchomić basiccx.exe program w wierszu polecenia, wprowadź **basiccx**.

   Ten program wyświetla ten tekst i kończy działanie:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
