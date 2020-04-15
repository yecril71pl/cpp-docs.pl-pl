---
title: Obsługa programu Clang/LLVM w projektach programu Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323121"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Obsługa clang/LLVM w projektach programu Visual Studio

::: moniker range="<=vs-2017"

Obsługa clang dla projektów CMake i MSBuild jest dostępna w programie Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Za pomocą programu Visual Studio 2019 w wersji 16.2 z clang można edytować, tworzyć i debugować projekty programu Visual Studio (MSBuild) przeznaczone dla systemu Windows lub Linux.

## <a name="install"></a>Instalowanie

Aby uzyskać najlepszą obsługę IDE w programie Visual Studio, zalecamy użycie najnowszych narzędzi kompilatora Clang dla systemu Windows. Jeśli jeszcze ich nie masz, możesz je zainstalować, otwierając Instalator programu Visual Studio i wybierając narzędzia Programu Visual Studio **Clang dla systemu Windows w** obszarze Tworzenie pulpitu z opcjonalnymi składnikami języka **C++.** Jeśli wolisz używać istniejącej instalacji Clang na swoim komputerze, wybierz **narzędzia do budowania języka C++ Clang-cl dla wersji 142.** opcjonalnego komponentu. Standardowa biblioteka microsoft c++ wymaga obecnie co najmniej clang 8.0.0; wiązana wersja Clang zostanie automatycznie zaktualizowana, aby być na bieżąco z aktualizacjami w implementacji biblioteki standardowej firmy Microsoft.

![Instalacja komponentu Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurowanie projektu systemu Windows do korzystania z narzędzi Clang

Aby skonfigurować projekt programu Visual Studio do używania programu Clang, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. Zazwyczaj należy najpierw wybrać **wszystkie konfiguracje** w górnej części okna dialogowego. Następnie, w obszarze **Ogólne** > **platformy Toolset**, wybierz **LLVM (clang-cl),** a następnie **OK**.

![Instalacja komponentu Clang](media/clang-msbuild-prop-page.png)

Jeśli używasz clang narzędzia, które są dołączone do programu Visual Studio, nie dodatkowe kroki są wymagane. W przypadku projektów systemu Windows program Visual Studio domyślnie wywołuje clang w trybie [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) i łączy się z implementacją biblioteki standardowej firmy Microsoft. Domyślnie **clang-cl.exe** znajduje `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`się w pliku .

Jeśli używasz niestandardowej instalacji Clang, możesz zmodyfikować**właściwości** >  **projektu** > **VC ++ DIrectories** > **Configuration Properties** > **Executable Directories,** dodając niestandardowy katalog `LLVMInstallDir` instalacji Clang jako pierwszy katalog lub zmienić wartość właściwości. Aby uzyskać więcej [informacji, zobacz Ustawianie niestandardowej lokalizacji LLVM.](#custom_llvm_location)

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurowanie projektu systemu Linux do korzystania z narzędzi Clang

W przypadku projektów systemu Linux program Visual Studio używa frontendu zgodnego z Clang GCC. Właściwości projektu i prawie wszystkie flagi kompilatora są identyczne

Aby skonfigurować projekt systemu Visual Studio Linux do używania programu Clang:

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**.
1. Zazwyczaj należy najpierw wybrać **wszystkie konfiguracje** w górnej części okna dialogowego.
1. W obszarze **Ogólne** > **narzędzie platformy ,** wybierz **WSL_Clang_1_0,** jeśli używasz podsystemu Systemu Windows dla systemu Linux, lub **Remote_Clang_1_0,** jeśli używasz komputera zdalnego lub maszyny wirtualnej.
1. Naciśnij przycisk **OK**.

![Instalacja komponentu Clang](media/clang-msbuild-prop-page.png)

W systemie Linux visual studio domyślnie używa pierwszej lokalizacji Clang, która napotka w path właściwości środowiska. Jeśli używasz niestandardowej instalacji Clang, należy `LLVMInstallDir` zmienić wartość właściwości lub zastąpić ścieżkę w obszarze**Właściwości** >  **projektu** > **VC ++ DIrectories** > Configuration**Properties** > **Executable Directories**. Aby uzyskać więcej [informacji, zobacz Ustawianie niestandardowej lokalizacji LLVM.](#custom_llvm_location)

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Ustawianie niestandardowej lokalizacji LLVM

Ścieżkę niestandardową llvm dla jednego lub więcej projektów można ustawić, tworząc plik *Directory.build.props* i dodając ten plik do folderu głównego dowolnego projektu. Można dodać go do głównego folderu rozwiązania, aby zastosować go do wszystkich projektów w rozwiązaniu. Plik powinien wyglądać tak (ale zastąpić rzeczywistą ścieżkę):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Ustawianie dodatkowych właściwości, edytowanie, tworzenie i debugowanie

Po skonfigurowaniu konfiguracji Clang kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Przeładuj projekt**. Teraz można tworzyć i debugować projekt za pomocą narzędzi Clang. Visual Studio wykrywa, że używasz kompilatora Clang i zapewnia IntelliSense, wyróżnianie, nawigację i inne funkcje edycji. Błędy i ostrzeżenia są wyświetlane w **oknie wyjściowym**. Strony właściwości projektu dla konfiguracji Clang są bardzo podobne do tych dla MSVC, chociaż niektóre funkcje zależne od kompilatora, takie jak Edit i Continue, nie są dostępne dla konfiguracji Clang. Aby ustawić opcję kompilatora lub konsolidatora Clang, która nie jest dostępna na stronach właściwości, można dodać ją ręcznie na stronach właściwości w obszarze **Właściwości** > konfiguracji**C/C++ (lub Konsolidator)** > **Opcje dodatkowe****wiersza** > polecenia .

Podczas debugowania można użyć punktów przerwania, wizualizacji pamięci i danych oraz większości innych funkcji debugowania.  

![Debugowanie clang](media/clang-debug-msbuild.png)

::: moniker-end
