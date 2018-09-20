---
title: '-FU (nazwij wymuszone #using) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e804aa48752d1f100e4c843fae9c0d5c70ae8b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423171"
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

Jeśli używasz języka C + +/ CLI i odwołują się do metadanych do użycia [przyjaznych zestawów](../../dotnet/friend-assemblies-cpp.md) funkcji, nie można użyć **/FU**. Za pomocą musi odwoływać się metadanych w kodzie `#using`— wraz z `[as friend]` atrybutu. Przyjazne zestawy nie są obsługiwane w Visual C++ składnika rozszerzenia C + +/ CX.

Aby uzyskać informacje o tym, jak utworzyć zestaw lub moduł, aby uzyskać środowisko uruchomieniowe języka wspólnego (CLR), zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md). Aby uzyskać informacje dotyczące sposobu tworzenia w języku C + +/ CX, zobacz [Kompilowanie aplikacji i bibliotek](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **życie #using** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)