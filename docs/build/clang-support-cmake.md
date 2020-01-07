---
title: Obsługa Clang/LLVM w projektach programu Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: b5a5985ad6a82d1c7ff45ceb3668273ec96292ec
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556724"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Obsługa Clang/LLVM w projektach programu Visual Studio CMake

::: moniker range="<=vs-2017"

Obsługa Clang jest dostępna w programie Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Możesz użyć programu Visual Studio z Clang do edytowania i debugowania C++ projektów CMAKE przeznaczonych dla systemu Windows lub Linux.

**System Windows**: program Visual Studio 2019 w wersji 16,1 obejmuje obsługę edytowania, kompilowania i debugowania z CLANG/LLVM w projektach cmake, które są przeznaczone dla systemu Windows.

**Linux**: for Linux CMAKE — nie jest wymagane żadne specjalne wsparcie dla programu Visual Studio. Możesz zainstalować Clang za pomocą Menedżera pakietów dystrybucji i dodać odpowiednie polecenia w pliku CMakeLists. txt.

## <a name="install"></a>Instalacja programu

Aby zapewnić najlepszą obsługę środowiska IDE w programie Visual Studio, zalecamy korzystanie z najnowszych narzędzi kompilatora Clang dla systemu Windows. Jeśli jeszcze tego nie zrobiono, można je zainstalować, otwierając Instalator programu Visual Studio i wybierając  **C++ kompilator Clang dla systemu Windows** w obszarze **Programowanie aplikacji klasycznych z C++**  opcjonalnymi składnikami. W przypadku korzystania z niestandardowej instalacji Clang należy sprawdzić składnik  **C++ Clang-CL for v142 Build Tools** .

![Instalacja składnika Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Utwórz nową konfigurację

Aby dodać nową konfigurację Clang do projektu CMake:

1. Kliknij prawym przyciskiem myszy CMakeLists. txt w **Eksplorator rozwiązań** i wybierz pozycję **CMAKE ustawienia dla projektu**.

1. W obszarze **konfiguracje**naciśnij przycisk **Dodaj konfigurację** :

   ![Dodawanie konfiguracji](media/cmake-add-config-icon.png)

1. Wybierz żądaną konfigurację Clang (należy zauważyć, że dla systemów Windows i Linux są dostarczane oddzielne konfiguracje Clang), a następnie naciśnij **pozycję Wybierz**:

   ![Konfiguracja CMake Clang](media/cmake-clang-configuration.png)

1. Aby wprowadzić modyfikacje w tej konfiguracji, użyj **edytora ustawień CMAKE**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień kompilacji CMAKE w programie Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Zmodyfikuj istniejącą konfigurację, aby użyć Clang

Aby zmodyfikować istniejącą konfigurację, aby użyć Clang, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy CMakeLists. txt w **Eksplorator rozwiązań** i wybierz pozycję **CMAKE ustawienia dla projektu**.

1. W obszarze **Ogólne** wybierz listę rozwijaną zestaw **narzędzi** i wybierz żądany zestaw narzędzi Clang:

   ![Zestaw narzędzi CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Niestandardowe lokalizacje Clang

Domyślnie program Visual Studio szuka Clang w dwóch miejscach:

- Systemy Zainstalowana wewnętrznie kopia Clang/LLVM, która jest dostarczana z instalatorem programu Visual Studio.
- (Systemy Windows i Linux) Zmienna środowiskowa PATH.

Możesz określić inną lokalizację, ustawiając zmienne **CMAKE_C_COMPILER** i **CMAKE_CXX_COMPILER** CMAKE w **ustawieniach CMAKE**:

![Zestaw narzędzi CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Tryby zgodności Clang

W przypadku konfiguracji systemu Windows CMake domyślnie wywołuje Clang w trybie [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) i łączy się z implementacją firmy Microsoft w warstwie Standardowa. Domyślnie **Clang-CL. exe** znajduje się w `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

 Te wartości można modyfikować w **ustawieniach CMAKE** w obszarze **zmienne CMAKE i pamięć podręczna**. Kliknij przycisk **Pokaż zaawansowane zmienne**. Przewiń w dół, aby znaleźć **CMAKE_CXX_COMPILER**, a następnie kliknij przycisk **Przeglądaj** , aby określić inną ścieżkę kompilatora.

## <a name="edit-build-and-debug"></a>Edytuj, Kompiluj i Debuguj

Po skonfigurowaniu konfiguracji Clang można skompilować i debugować projekt. Program Visual Studio wykrywa, że używasz kompilatora Clang i udostępnia funkcję IntelliSense, wyróżnianie, nawigację i inne funkcje edycji. Błędy i ostrzeżenia są wyświetlane w **okno dane wyjściowe**.

Podczas debugowania można użyć punktów przerwania, pamięci i wizualizacji danych oraz większości innych funkcji debugowania. Niektóre funkcje zależne od kompilatora, takie jak Edit i Continue, nie są dostępne do konfiguracji Clang.

![Debugowanie CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
