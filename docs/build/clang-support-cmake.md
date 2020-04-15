---
title: Obsługa clang/LLVM w projektach CMake programu Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323177"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Obsługa clang/LLVM w projektach CMake programu Visual Studio

::: moniker range="<=vs-2017"

Pomoc techniczna clang jest dostępna w programie Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio z clang można edytować i debugować C++ CMake projektów, które są przeznaczone dla systemu Windows lub Linux.

**Windows**: Visual Studio 2019 w wersji 16.1 zawiera obsługę edycji, tworzenia i debugowania z Clang/LLVM w CMake projektów przeznaczonych dla systemu Windows.

**Linux**: Dla projektów Linux CMake nie jest wymagana specjalna obsługa programu Visual Studio. Możesz zainstalować Clang za pomocą menedżera pakietów swojej dystrybucji i dodać odpowiednie polecenia w pliku CMakeLists.txt.

## <a name="install"></a>Instalowanie

Aby uzyskać najlepszą obsługę IDE w programie Visual Studio, zalecamy użycie najnowszych narzędzi kompilatora Clang dla systemu Windows. Jeśli jeszcze ich nie masz, możesz je zainstalować, otwierając Instalator programu Visual Studio i wybierając **kompilator programu C++ Clang dla systemu Windows w** obszarze Tworzenie pulpitu z opcjonalnymi składnikami języka **C++.** Podczas korzystania z niestandardowej instalacji Clang, sprawdź **C++ Clang-cl dla v142 składnik narzędzi kompilacji.**

![Instalacja komponentu Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Tworzenie nowej konfiguracji

Aby dodać nową konfigurację Clang do projektu CMake:

1. Kliknij prawym przyciskiem myszy CMakeLists.txt w **Eksploratorze rozwiązań** i wybierz **CMake ustawienia projektu**.

1. W obszarze **Konfiguracje**naciśnij przycisk **Dodaj konfigurację:**

   ![Dodawanie konfiguracji](media/cmake-add-config-icon.png)

1. Wybierz żądaną konfigurację Clang (zwróć uwagę, że oddzielne konfiguracje Clang są dostępne dla Windows i Linux), a następnie naciśnij **select:**

   ![Konfiguracja CMake Clang](media/cmake-clang-configuration.png)

1. Aby wprowadzić zmiany w tej konfiguracji, użyj **Edytora ustawień CMake**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień kompilacji CMake w programie Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modyfikowanie istniejącej konfiguracji w celu użycia programu Clang

Aby zmodyfikować istniejącą konfigurację w celu użycia Clang, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy CMakeLists.txt w **Eksploratorze rozwiązań** i wybierz **CMake ustawienia projektu**.

1. W **obszarze Ogólne** wybierz rozwijany zestaw **narzędzi** i wybierz żądany zestaw narzędzi Clang:

   ![Zestaw narzędzi CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Niestandardowe lokalizacje clangów

Domyślnie Visual Studio wyszukuje Clang w dwóch miejscach:

- (Windows) Wewnętrznie zainstalowana kopia Clang/LLVM, która jest dostępna z instalatorem programu Visual Studio.
- (Windows i Linux) Zmienna środowiskowa PATH.

Można określić inną lokalizację, ustawiając **zmienne CMAKE_C_COMPILER** i **CMAKE_CXX_COMPILER** CMake w **ustawieniach CMake:**

![Zestaw narzędzi CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Tryby zgodności clang

W przypadku konfiguracji systemu Windows CMake domyślnie wywołuje Clang w trybie [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) i łączy się z implementacją biblioteki standardowej firmy Microsoft. Domyślnie **clang-cl.exe** znajduje `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`się w pliku .

Można zmodyfikować te wartości w **CMake Ustawienia** w obszarze **CMake zmiennych i pamięci podręcznej**. Kliknij **pozycję Pokaż zmienne zaawansowane**. Przewiń w dół, aby znaleźć **CMAKE_CXX_COMPILER**, a następnie kliknij przycisk **Przeglądaj,** aby określić inną ścieżkę kompilatora.

## <a name="edit-build-and-debug"></a>Edytowanie, tworzenie i debugowanie

Po skonfigurowaniu konfiguracji Clang, można tworzyć i debugować projekt. Visual Studio wykrywa, że używasz kompilatora Clang i zapewnia IntelliSense, wyróżnianie, nawigację i inne funkcje edycji. Błędy i ostrzeżenia są wyświetlane w **oknie wyjściowym**.

Podczas debugowania można użyć punktów przerwania, wizualizacji pamięci i danych oraz większości innych funkcji debugowania. Niektóre funkcje zależne od kompilatora, takie jak Edycja i Kontynuuj, nie są dostępne dla konfiguracji Clang.

![Debugowanie CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
