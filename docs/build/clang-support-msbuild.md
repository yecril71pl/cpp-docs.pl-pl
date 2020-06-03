---
title: Obsługa Clang/LLVM w projektach programu Visual Studio Visual Studio
ms.date: 06/02/2020
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 1a1dfef033bffd3d7f1d24233752d7beae11af8e
ms.sourcegitcommit: d695bb727bd2b081af4d50127b0242a9a5bdce61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84332282"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Obsługa Clang/LLVM w projektach programu Visual Studio

::: moniker range="<=vs-2017"

Obsługa Clang dla projektów CMake i MSBuild jest dostępna w programie Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Aby edytować, kompilować i debugować projekty języka Visual Studio (MSBuild) przeznaczone dla systemu Windows lub Linux, można użyć programu Visual Studio 2019 w wersji 16,2 z Clang.

## <a name="install"></a>Zainstaluj

Aby zapewnić najlepszą obsługę środowiska IDE w programie Visual Studio, zalecamy korzystanie z najnowszych narzędzi kompilatora Clang dla systemu Windows. Jeśli jeszcze tego nie zrobiono, możesz je zainstalować, otwierając Instalator programu Visual Studio i wybierając **C++ Clang Tools for Windows** w obszarze **Programowanie aplikacji klasycznych za pomocą** opcjonalnych składników języka c++. Jeśli wolisz używać istniejącej instalacji Clang na maszynie, wybierz opcję **C++ Clang-CL dla v142 Build Tools.** składnik opcjonalny. Biblioteka standardowa Microsoft C++ wymaga obecnie co najmniej Clang 8.0.0; wersja pakietu Clang zostanie automatycznie zaktualizowana tak, aby zachować aktualność z aktualizacjami w ramach implementacji standardowej biblioteki firmy Microsoft.

![Instalacja składnika Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurowanie projektu systemu Windows do korzystania z narzędzi Clang

Aby skonfigurować projekt programu Visual Studio do korzystania z Clang, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Zazwyczaj należy najpierw wybrać **wszystkie konfiguracje** w górnej części okna dialogowego. Następnie w obszarze **Ogólne**zestawy  >  **narzędzi platformy**wybierz pozycję **LLVM (Clang-CL)** , a następnie kliknij **przycisk OK**.

![Instalacja składnika Clang](media/clang-msbuild-prop-page.png)

Jeśli używasz narzędzi Clang, które są powiązane z programem Visual Studio, nie są wymagane żadne dodatkowe czynności. W przypadku projektów systemu Windows program Visual Studio domyślnie wywołuje Clang w trybie [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) i łączy z implementacją firmy Microsoft w warstwie Standardowa. Domyślnie **Clang-CL. exe** znajduje się w lokalizacji *% VCINSTALLDIR% \\ Tools \\ LLVM \\ bin \\ * i *% VCINSTALLDIR% \\ Tools \\ LLVM \\ x x64 \\ \\ *.

W przypadku korzystania z niestandardowej instalacji Clang można zmodyfikować właściwości **projektu**  >  **Properties**  >  pliki konfiguracji**katalogów VC + +** katalogów  >  **Configuration Properties**  >  **wykonywalnych** przez dodanie niestandardowego katalogu instalacji Clang jako pierwszy katalog lub zmienić wartość `LLVMInstallDir` właściwości. Aby uzyskać więcej informacji [, zobacz Ustawianie niestandardowej lokalizacji LLVM](#custom_llvm_location) .

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurowanie projektu systemu Linux do korzystania z narzędzi Clang

W przypadku projektów systemu Linux program Visual Studio używa frontonu zgodnego ze standardem Clang. Właściwości projektu i niemal wszystkie flagi kompilatora są identyczne

Aby skonfigurować projekt programu Visual Studio Linux do korzystania z Clang:

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.
1. Zazwyczaj należy najpierw wybrać **wszystkie konfiguracje** w górnej części okna dialogowego.
1. W obszarze **Ogólne zestawy** > **narzędzi platformy**wybierz **WSL_Clang_1_0** , jeśli używasz podsystemu Windows dla systemu Linux lub **Remote_Clang_1_0** , jeśli używasz maszyny zdalnej lub maszyny wirtualnej.
1. Naciśnij przycisk **OK**.

![Instalacja składnika Clang](media/clang-msbuild-prop-page.png)

W systemie Linux program Visual Studio domyślnie używa pierwszej lokalizacji Clang, która napotka we właściwości środowisko ścieżki. W przypadku korzystania z niestandardowej instalacji Clang należy zmienić wartość `LLVMInstallDir` właściwości lub zastąpić ścieżkę w obszarze właściwości **projektu**  >  **Properties**  >  pliki konfiguracji**katalogów VC + +**  >  **Configuration Properties**  >  **Executable Directories**. Aby uzyskać więcej informacji [, zobacz Ustawianie niestandardowej lokalizacji LLVM](#custom_llvm_location) .

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Ustawianie niestandardowej lokalizacji LLVM

Możesz ustawić niestandardową ścieżkę dla LLVM dla jednego lub wielu projektów, tworząc plik *Directory. Build. props* i dodając ten plik do folderu głównego dowolnego projektu. Możesz dodać go do folderu rozwiązania głównego, aby zastosować go do wszystkich projektów w rozwiązaniu. Plik powinien wyglądać następująco (ale zastąpić rzeczywistą ścieżkę):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Ustaw dodatkowe właściwości, Edytuj, Kompiluj i Debuguj

Po skonfigurowaniu konfiguracji Clang kliknij prawym przyciskiem myszy w węźle projektu i wybierz polecenie **Załaduj ponownie projekt**. Teraz można kompilować i debugować projekt przy użyciu narzędzi Clang. Program Visual Studio wykrywa, że używasz kompilatora Clang i udostępnia funkcję IntelliSense, wyróżnianie, nawigację i inne funkcje edycji. Błędy i ostrzeżenia są wyświetlane w **okno dane wyjściowe**. Strony właściwości projektu dla konfiguracji Clang są bardzo podobne do tych dla MSVC, mimo że niektóre funkcje zależne od kompilatora, takie jak Edit i Continue, nie są dostępne dla konfiguracji Clang. Aby ustawić kompilator Clang lub opcję konsolidatora, która nie jest dostępna na stronach właściwości, można dodać ją ręcznie na stronach właściwości w obszarze **Właściwości konfiguracji**  >  **C/C++ (lub konsolidator)**  >  **Command Line**  >  **opcji Opcje dodatkowe**.

Podczas debugowania można użyć punktów przerwania, pamięci i wizualizacji danych oraz większości innych funkcji debugowania.  

![Debugowanie Clang](media/clang-debug-msbuild.png)

::: moniker-end
