---
title: /LIBPATH (Dodatkowa Libpath)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: ab586c788825a854e7d3cb3760da6e4e5558de3a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819886"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **dodatkowe katalogi bibliotek** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
