---
title: Tworzenie projektu CMake systemu Linux w programie Visual Studio
description: Jak utworzyć projekt systemu Linux CMake w programie Visual Studio
ms.date: 08/06/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 1b622bcd2af49ee51f7546be4c7a6d804c3102d0
ms.sourcegitcommit: 2034f8e744a8b36cff8b15e9a5cfe684afebadfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2020
ms.locfileid: "88043827"
---
# <a name="create-a-cmake-linux-project-in-visual-studio"></a>Tworzenie projektu CMake systemu Linux w programie Visual Studio

::: moniker range="vs-2015"
Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych. Aby wyświetlić dokumentację dla tych wersji, Ustaw listę rozwijaną **wersja** znajdującą się powyżej spisu treści w **programie Visual Studio 2017** lub **Visual Studio 2019**.
::: moniker-end

::: moniker range=">=vs-2017"

Zalecamy używanie CMake na potrzeby projektów, które są na wielu platformach lub będą udostępniane jako "open source". Projektów CMake można użyć do kompilowania i debugowania tego samego kodu źródłowego w systemie Windows, podsystemu Windows dla systemu Linux (WSL) i systemów zdalnych.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Najpierw upewnij się, że masz zainstalowane obciążenie programu Visual Studio Linux, w tym składnik CMake. To jest programowanie dla systemu **Linux przy użyciu obciążenia C++** w Instalatorze programu Visual Studio. Zapoznaj się z tematem [Instalowanie obciążenia C++ systemu Linux w programie Visual Studio](download-install-and-setup-the-linux-development-workload.md) , jeśli nie masz pewności, że zainstalowano program.

Upewnij się również, że na komputerze zdalnym są zainstalowane następujące elementy:

- zatoce
- GDB
- rsync
- kodu
- Ninja — kompilacja (Visual Studio 2019 lub nowsza)
::: moniker-end

::: moniker range="vs-2017"
Obsługa CMake w programie Visual Studio wymaga obsługi trybu serwera wprowadzonej w CMake 3,8. W przypadku CMake z wariantem dostarczonym przez firmę Microsoft Pobierz najnowsze wstępnie skompilowane pliki binarne w [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

Pliki binarne są instalowane w programie `~/.vs/cmake` . Po wdrożeniu plików binarnych projekt zostanie automatycznie replikny. Jeśli CMake określony przez `cmakeExecutable` pole w *CMakeSettings.json* jest nieprawidłowy (nie istnieje lub jest nieobsługiwaną wersją), a wstępnie skompilowane pliki binarne są obecne, program Visual Studio ignoruje `cmakeExecutable` i używa wstępnie skompilowanych plików binarnych.

Program Visual Studio 2017 nie może utworzyć projektu CMake od podstaw, ale można otworzyć folder zawierający istniejący projekt CMake, zgodnie z opisem w następnej sekcji.
::: moniker-end

::: moniker range=">=vs-2019"
Możesz użyć programu Visual Studio 2019 do kompilowania i debugowania w zdalnym systemie Linux lub WSL, a CMake zostanie wywołana w tym systemie. Na maszynie docelowej należy zainstalować CMAKE w wersji 3,14 lub nowszej.

Upewnij się, że na komputerze docelowym jest używana najnowsza wersja programu CMake. Często Wersja oferowana przez domyślny Menedżer pakietów dystrybucji nie jest wystarczająca do obsługi wszystkich funkcji wymaganych przez program Visual Studio. Program Visual Studio 2019 wykrywa, czy w systemie Linux jest zainstalowana najnowsza wersja programu CMake. Jeśli nie zostanie znaleziona, program Visual Studio wyświetli pasek informacji w górnej części okienka edytora. Oferuje ona możliwość instalacji CMake z programu [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

W programie Visual Studio 2019 można utworzyć projekt CMake od podstaw lub otworzyć istniejący projekt CMake. Aby utworzyć nowy projekt CMake, postępuj zgodnie z poniższymi instrukcjami. Lub przejdź z wyprzedzeniem, aby [otworzyć folder projektu CMAKE](#open-a-cmake-project-folder) , jeśli istnieje już projekt CMAKE.

## <a name="create-a-new-linux-cmake-project"></a>Tworzenie nowego projektu CMake systemu Linux

Aby utworzyć nowy projekt systemu Linux CMake w programie Visual Studio 2019:

1. Wybierz pozycję **plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Ustaw **Język** na **C++** i wyszukaj ciąg "CMAKE". Następnie wybierz przycisk **dalej**. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz pozycję **Utwórz**.

Alternatywnie możesz otworzyć własny projekt CMake w programie Visual Studio 2019. W poniższej sekcji wyjaśniono, jak.

Program Visual Studio tworzy plik o minimalnym *CMakeLists.txt* tylko przy użyciu nazwy pliku wykonywalnego i minimalnej wymaganej wersji CMAKE. Możesz jednak ręcznie edytować ten plik. Program Visual Studio nigdy nie zastąpi zmian.

Aby ułatwić zrozumienie, edytowanie i tworzenie skryptów CMake w programie Visual Studio 2019, zapoznaj się z następującymi zasobami:

- [Dokumentacja w edytorze dla CMake w programie Visual Studio](https://devblogs.microsoft.com/cppblog/in-editor-documentation-for-cmake-in-visual-studio/)
- [Nawigacja po kodzie dla skryptów CMake](https://devblogs.microsoft.com/cppblog/code-navigation-for-cmake-scripts/)
- [Łatwe dodawanie, usuwanie i zmiana nazw plików i obiektów docelowych w projektach CMake](https://devblogs.microsoft.com/cppblog/easily-add-remove-and-rename-files-and-targets-in-cmake-projects/)
::: moniker-end

::: moniker range=">=vs-2017"
## <a name="open-a-cmake-project-folder"></a>Otwieranie folderu projektu CMake

Po otwarciu folderu zawierającego istniejący projekt CMake program Visual Studio używa zmiennych w pamięci podręcznej CMake, aby automatycznie konfigurować funkcje IntelliSense i kompilacje. Ustawienia konfiguracji lokalnej i debugowania są przechowywane w plikach JSON. Możesz opcjonalnie udostępniać te pliki innym osobom korzystającym z programu Visual Studio.

Program Visual Studio nie modyfikuje plików *CMakeLists.txt* . Pozwala to innym osobom pracującym nad tym samym projektem w dalszym ciągu korzystać z istniejących narzędzi. Program Visual Studio generuje ponownie pamięć podręczną podczas zapisywania zmian w *CMakeLists.txt*lub w niektórych przypadkach, aby *CMakeSettings.jsna*. W przypadku korzystania z **istniejącej konfiguracji pamięci** podręcznej program Visual Studio nie modyfikuje pamięci podręcznej.

Aby uzyskać ogólne informacje na temat obsługi CMake w programie Visual Studio, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md). Przeczytaj ten element przed kontynuowaniem.

Aby rozpocząć, wybierz pozycję **plik**  >  **Otwórz**  >  **folder** z menu głównego lub inny typ `devenv.exe <foldername>` w oknie [wiersza polecenia dewelopera](../build/building-on-the-command-line.md) . Otwarty folder powinien zawierać plik *CMakeLists.txt* wraz z kodem źródłowym.

W poniższym przykładzie przedstawiono prosty plik *CMakeLists.txt* i plik. cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu CMake systemu Linux](cmake-linux-configure.md)

## <a name="see-also"></a>Zobacz także

[CMake projekty w programie Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
::: moniker-end
