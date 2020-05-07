---
title: 'Wskazówki: kompilowanie programu w języku C++/CX w wierszu polecenia'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078206"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Wskazówki: kompilowanie programu w języku C++/CX w wierszu polecenia

> [!NOTE]
> W przypadku nowych aplikacji i składników platformy UWP zaleca się używanie języka [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/), czyli standardowego wyrzutowania języka c++ 17 dla środowisko wykonawcze systemu Windows interfejsów API. C++/WinRT jest dostępna w zestawie SDK systemu Windows 10 w wersji 1803. Język C++/WinRT jest implementowany całkowicie w plikach nagłówkowych i został zaprojektowany w celu zapewnienia pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows.

Kompilator języka Microsoft C++ (MSVC) obsługuje rozszerzenia składników C++ (C++/CX), które mają dodatkowe typy i operatory przeznaczone dla modelu programowania środowisko wykonawcze systemu Windows. Za pomocą języka C++/CX można tworzyć aplikacje dla platforma uniwersalna systemu Windows (platformy UWP) i pulpitu systemu Windows. Aby uzyskać więcej informacji, zobacz [Przewodnik po C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) i [rozszerzenia składników dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

W tym instruktażu należy użyć edytora tekstów do utworzenia podstawowego programu C++/CX, a następnie skompilowania go w wierszu polecenia. (Możesz użyć własnego programu C++/CX zamiast wpisywać ten, który jest wyświetlany, lub możesz użyć przykładowego kodu C++/CX z innego artykułu pomocy. Ta technika jest przydatna do kompilowania i testowania małych modułów, które nie mają elementów interfejsu użytkownika.

> [!NOTE]
> Do kompilowania programów C++/CX można także użyć środowiska IDE programu Visual Studio. Ze względu na to, że IDE obejmuje obsługę projektowania, debugowania, emulacji i wdrażania, która nie jest dostępna w wierszu polecenia, zaleca się używanie środowiska IDE do kompilowania aplikacji platforma uniwersalna systemu Windows (platformy UWP). Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji platformy UWP w języku C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Wymagania wstępne

Rozumiesz podstawy języka C++.

## <a name="compiling-a-ccx-program"></a>Kompilowanie programu w języku C++/CX

Aby włączyć kompilację dla/CX C++, należy użyć opcji kompilatora [/zw](reference/zw-windows-runtime-compilation.md) . Kompilator MSVC generuje plik. exe, który jest przeznaczony dla środowisko wykonawcze systemu Windows, oraz linki do wymaganych bibliotek.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Aby skompilować aplikację C++/CX w wierszu polecenia

1. Otwórz okno **wiersz polecenia dla deweloperów** . (W oknie **uruchamiania** Otwórz pozycję **aplikacje**. Otwórz folder **Visual Studio Tools** w używanej wersji programu Visual Studio, a następnie wybierz skrót **wiersz polecenia dla deweloperów** .) Aby uzyskać więcej informacji na temat otwierania okna wiersz polecenia dla deweloperów, zobacz Korzystanie z zestawu [narzędzi MSVC w wierszu polecenia](building-on-the-command-line.md).

   Do pomyślnego skompilowania kodu w zależności od systemu operacyjnego i konfiguracji komputera może być wymagane poświadczenie administratora. Aby uruchomić okno wiersza polecenia jako administrator, otwórz menu skrótów dla **wiersz polecenia dla deweloperów** a następnie wybierz **Uruchom jako administrator**.

1. W wierszu polecenia wprowadź **Notepad basiccx. cpp**.

   Wybierz opcję **tak** po wyświetleniu monitu o utworzenie pliku.

1. W Notatniku wprowadź następujące wiersze:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Na pasku menu wybierz **plik** > **Zapisz**.

   Utworzono plik źródłowy języka C++, który używa przestrzeni nazw środowisko wykonawcze systemu Windows [platformy przestrzeni nazw](../cppcx/platform-namespace-c-cx.md) .

1. W wierszu polecenia wprowadź ciąg **CL/EHSC/zw basiccx. cpp/link/SUBSYSTEM: Console**. Kompilator CL. exe kompiluje kod źródłowy do pliku. obj, a następnie uruchamia konsolidator w celu wygenerowania programu wykonywalnego o nazwie basiccx. exe. (Opcja kompilatora [/EHsc](reference/eh-exception-handling-model.md) Określa model obsługi wyjątków C++, a flaga [/link](reference/link-pass-options-to-linker.md) określa aplikację konsolową).

1. Aby uruchomić program basiccx. exe, w wierszu polecenia wpisz **basiccx**.

   Program wyświetla ten tekst i opuszcza:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Zobacz też

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
