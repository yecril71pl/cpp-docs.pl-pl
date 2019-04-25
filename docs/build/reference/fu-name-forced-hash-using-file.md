---
title: '/FU (Nazwij wymuszone pliki dyrektywy #using)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: c47a45208ac5b5c7e0000516ed114c008feda7ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292292"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nazwij wymuszone pliki dyrektywy #using)

Opcję kompilatora, która służy jako alternatywę do przekazywania nazwę pliku do [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) w kodzie źródłowym.

## <a name="syntax"></a>Składnia

> **/Fu** *pliku*

## <a name="arguments"></a>Argumenty

*Plik*<br/>
Określa plik metadanych, aby odwołać się w tej kompilacji.

## <a name="remarks"></a>Uwagi

Przełącznik /FU trwa tylko jedną nazwę pliku. Do określenia wielu plików, za pomocą /FU każdej z nich.

Jeśli używasz C++/interfejsu wiersza polecenia oraz że odwołuje się do metadanych do użycia [przyjaznych zestawów](../../dotnet/friend-assemblies-cpp.md) funkcji, nie można użyć **/FU**. Za pomocą musi odwoływać się metadanych w kodzie `#using`— wraz z `[as friend]` atrybutu. Przyjazne zestawy nie są obsługiwane w elemencie wizualnym C++ rozszerzenia składnika C++/CX.

Aby uzyskać informacje o tym, jak utworzyć zestaw lub moduł, aby uzyskać środowisko uruchomieniowe języka wspólnego (CLR), zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md). Aby uzyskać informacje dotyczące sposobu tworzenia C++/CX, zobacz [Kompilowanie aplikacji i bibliotek](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **życie #using** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
