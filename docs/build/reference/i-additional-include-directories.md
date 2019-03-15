---
title: /I (dodatkowe katalogi dołączenia)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 6ec8b15e77fec5214013c484e617904ed29e8197
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807640"
---
# <a name="i-additional-include-directories"></a>/I (dodatkowe katalogi dołączenia)

Dodaje katalog do listy katalogi przeszukiwane w poszukiwaniu plików dołączanych.

## <a name="syntax"></a>Składnia

> **/I**[*katalogu*

### <a name="arguments"></a>Argumenty

*directory*<br/>
Katalog, który ma zostać dodany do listy katalogów wyszukiwane dołączane pliki.

## <a name="remarks"></a>Uwagi

Aby dodać więcej niż jeden katalog, użyj tej opcji więcej niż jeden raz. Przeszukiwane są katalogi, aż zostanie znaleziony określonegop dołączanego pliku.

Można użyć tej opcji z ([/X (Ignoruj standardowe ścieżki dołączanych plików)](x-ignore-standard-include-paths.md)) opcji.

Kompilator przeszukuje katalogi w następującej kolejności:

1. Jeśli zostanie określony, przy użyciu [# dyrektywy include](../../preprocessor/hash-include-directive-c-cpp.md) w formie podwójnego cudzysłowu, najpierw przeszukuje katalogi lokalne. Wyszukiwanie rozpoczyna się w tym samym katalogu co plik, który zawiera **#include** instrukcji. W przypadku niepowodzenia można znaleźć pliku wyszukiwania w wszelkich aktualnie otwartych katalogów Dołącz pliki, w odwrotnej kolejności, w jakiej zostały otwarte. Wyszukiwanie rozpoczyna się w katalogu nadrzędnego dołączyć plik i jest kontynuowane w górę przez katalogi stojących dołączyć pliki.

1. Jeśli zostanie określony, przy użyciu **#include** dyrektywy w kąt Dopasowywanie formularza lub jeśli wyszukiwania w katalogu lokalnym zakończyło się niepowodzeniem, przeszukuje katalogi określone za pomocą **/I** opcji, w kolejności CL napotka je w wierszu polecenia.

1. Katalogi określone w **INCLUDE** zmiennej środowiskowej.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

1. Modyfikowanie **dodatkowe katalogi dołączenia** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Przykład

Następujące polecenie szuka plików dołączanych, żądane przez MAIN.c w następującej kolejności: Po pierwsze Jeśli określony, przy użyciu podwójnych cudzysłowów, przeszukiwane są pliki lokalne. Następnie wyszukiwanie jest kontynuowane w katalogu \INCLUDE, a następnie w katalogu \MY\INCLUDE i na koniec w katalogach przypisany do zmiennej środowiskowej INCLUDE.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
