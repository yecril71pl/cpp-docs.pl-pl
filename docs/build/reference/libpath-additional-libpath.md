---
title: -LIBPATH (dodatkowa Libpath) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784281df23b0a8d43625766297b6cbbd20179c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717200"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Dodatkowa Libpath)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Parametry

*dir*<br/>
Określa ścieżkę, konsolidator wyszuka przed wyszukuje w ścieżce określonej w opcji środowiska LIB.

## <a name="remarks"></a>Uwagi

Opcja/libpath — umożliwia zastąpienie ścieżki biblioteki środowiska. Konsolidator najpierw wyszukać w ścieżce określonej przez tę opcję, a następnie wyszukaj w ścieżce określonej w zmiennej środowiskowej LIB. Można określić tylko jeden katalog dla każdej opcji/libpath —, które można wprowadzić. Jeśli chcesz określić więcej niż jeden katalog, należy określić wiele opcji/libpath —. Program łączący następnie wyszukiwanie określonych katalogach w kolejności.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **dodatkowe katalogi bibliotek** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)