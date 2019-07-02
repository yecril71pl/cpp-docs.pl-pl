---
title: Obsługa clang/LLVM w projektach CMake usługi Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518167"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Obsługa clang/LLVM w projektach CMake usługi Visual Studio

::: moniker range="<=vs-2017"

Clang pomoc techniczna jest dostępna w programie Visual Studio 2019 r.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio z Clang służy do edytowania i debugowania C++ CMake projektów tego target Windows lub Linux.

**Windows**: Visual Studio 2019 16.1 wersja obejmuje obsługę edycji, kompilowania i debugowania przy użyciu Clang/LLVM w projektach CMake przeznaczonych dla Windows. 

**Linux**: W przypadku projektów CMake systemu Linux specjalne obsługi programu Visual Studio jest wymagany. Instalovat Clang przy użyciu Menedżera pakietów w Twojej dystrybucji i dodaj odpowiednie polecenia w pliku CMakeLists.txt.

## <a name="install"></a>Zainstaluj

Obsługę najlepsze środowisko IDE w programie Visual Studio zaleca się przy użyciu najnowszych narzędzi Clang w kompilatorze dla Windows. Jeśli nie masz jeszcze tych, możesz je zainstalować, korzystając z otwierając Instalatora programu Visual Studio i wybierając polecenie **Clang kompilatora dla Windows** w obszarze **programowanie aplikacji klasycznych przy użyciu C++**  opcjonalnych składników.

![Instalacja składnika clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Utwórz nową konfigurację

Aby dodać nową konfigurację Clang do projektu narzędzia CMake:

1. Kliknij prawym przyciskiem myszy w pliku CMakeLists.txt w **Eksploratora rozwiązań** i wybierz polecenie **ustawienia narzędzia CMake dla projektu**.

1. W obszarze **konfiguracje**, naciśnij klawisz **Dodawanie konfiguracji** przycisku:

   ![Dodaj konfigurację](media/cmake-add-config-icon.png)

1. Wybierz żądaną konfiguracją Clang (Zauważ, że oddzielne konfiguracje Clang są udostępniane dla Windows i Linux), naciśnij klawisz **wybierz**:

   ![Konfiguracja narzędzia CMake, Clang](media/cmake-clang-configuration.png)

1. Aby wprowadzić zmiany w tej konfiguracji, należy użyć **edytora ustawienia narzędzia CMake**. Aby uzyskać więcej informacji, zobacz [ustawień w programie Visual Studio kompilacji CMake dostosować](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modyfikuj istniejącą konfigurację, aby użyć Clang

Aby zmodyfikować istniejącą konfigurację, aby użyć Clang, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy w pliku CMakeLists.txt w **Eksploratora rozwiązań** i wybierz polecenie **ustawienia narzędzia CMake dla projektu**.

1. W obszarze **ogólne** wybierz **narzędzi** listy rozwijanej i wybierz żądany zestaw narzędzi Clang:

   ![Zestaw narzędzi Clang narzędzia CMake](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Niestandardowe lokalizacje Clang

Domyślnie program Visual Studio szuka Clang w dwóch miejscach:

- (Windows) Wewnętrznie zainstalowana kopia programu Clang/LLVM, który jest dostarczany z Instalatorem programu Visual Studio.
- (Windows i Linux) Zmiennej środowiskowej PATH.

Można określić inną lokalizację, ustawiając **CMAKE_C_COMPILER** i **CMAKE_CXX_COMPILER** zmienne narzędzia CMake w **ustawienia narzędzia CMake**:

![Zestaw narzędzi Clang narzędzia CMake](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang trybów zgodności

W przypadku konfiguracji z Windows CMake domyślnie wywołuje Clang w [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) tryb i łącza z implementacją Microsoft standardowej biblioteki. Domyślnie **clang cl.exe** znajduje się w `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

 Możesz zmodyfikować te wartości w **ustawienia narzędzia CMake** w obszarze **CMake zmiennych i pamięci podręcznej**. Kliknij przycisk **Pokaż zaawansowane zmienne**. Przewiń w dół do znajdowania **CMAKE_CXX_COMPILER**, następnie kliknij przycisk **Przeglądaj** przycisk, aby określić ścieżkę innego kompilatora.

## <a name="edit-build-and-debug"></a>Edycji, kompilowania i debugowania

Po skonfigurowaniu konfiguracji Clang można tworzyć i debugować projekt. Program Visual Studio wykryje, że używasz kompilatora Clang i oferuje funkcję IntelliSense, wyróżnianie nawigacji i inne funkcje edycji. Błędy i ostrzeżenia są wyświetlane w **okno danych wyjściowych**.

Podczas debugowania, możesz użyć punktów przerwania, pamięci i wizualizacji danych i większości innych funkcji debugowania. Niektóre funkcje kompilatora zależne, takie jak Edytuj i Kontynuuj nie są dostępne dla konfiguracji Clang.

![CMake Clang debugowania](media/clang-debug-visualize.png)

::: moniker-end
