---
title: -I (dodatkowe katalogi dołączenia) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a580488650a1272ec1dffcd1f0ba27c736df92da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705344"
---
# <a name="i-additional-include-directories"></a>/I (Dodatkowe katalogi dołączenia)

Dodaje katalog do listy katalogi przeszukiwane w poszukiwaniu plików dołączanych.

## <a name="syntax"></a>Składnia

```
/I[ ]directory
```

## <a name="arguments"></a>Argumenty

*Katalog*<br/>
Katalog, który ma zostać dodany do listy katalogów wyszukiwane dołączane pliki.

## <a name="remarks"></a>Uwagi

Aby dodać więcej niż jeden katalog, użyj tej opcji więcej niż jeden raz. Przeszukiwane są katalogi, aż zostanie znaleziony określonegop dołączanego pliku.

Za pomocą tej opcji Ignore Standard Include Paths ([/X (Ignoruj standardowe ścieżki dołączanych plików)](../../build/reference/x-ignore-standard-include-paths.md)) opcji.

Kompilator wyszukuje katalogi, w następującej kolejności:

1. Katalogi zawierające pliku źródłowego.

1. Katalogi określone za pomocą **/I** opcji, w kolejności CL napotka je.

1. Katalogi określone w **INCLUDE** zmiennej środowiskowej.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **dodatkowe katalogi dołączenia** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Przykład

Następujące polecenie szuka plików dołączanych, żądane przez MAIN.c w następującej kolejności: pierwsza na katalog zawierający MAIN.c, następnie w katalogu \INCLUDE, a następnie w katalogu \MY\INCLUDE i na koniec w katalogach przypisane do DOŁĄCZENIA zmiennej środowiskowej.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)