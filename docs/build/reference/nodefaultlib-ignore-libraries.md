---
title: /NODEFAULTLIB (Ignoruj biblioteki)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: 12a6e988828d1e4e2dbdc46d49da5ff2fe9e9d8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473779"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignoruj biblioteki)

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>Argumenty

*Biblioteka*<br/>
Biblioteka, która ma konsolidator, aby ignorować podczas rozpoznawania odwołań zewnętrznych.

## <a name="remarks"></a>Uwagi

Opcja/nodefaultlib informuje konsolidator, aby usunąć co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.

Aby utworzyć pliku .obj, który nie zawiera odwołania do bibliotek domyślnych, użyj [/Zl (Pomiń domyślną nazwę biblioteki)](../../build/reference/zl-omit-default-library-name.md).

Domyślnie/nodefaultlib usuwa wszystkie domyślne biblioteki z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. Opcjonalny *biblioteki* parametr pozwala usunąć określonej biblioteki lub biblioteki z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych. Określ jedną z opcji/nodefaultlib bibliotek, które chcesz wykluczyć.

Konsolidator usuwa odwołań na definicje zewnętrzne, wyszukując najpierw w bibliotekach, które zostaną jawnie określone, a następnie w domyślnych bibliotek określony za pomocą opcji /DEFAULTLIB, a następnie na domyślne biblioteki o nazwie w plikach .obj.

/ NODEFAULTLIB:*biblioteki* zastępuje [/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*biblioteki* gdy takie same *biblioteki* nazwa jest określona w obu.

Użycie opcji/nodefaultlib, na przykład do tworzenia programu bez biblioteki wykonawczej C, może być konieczne także użyć [/Entry](../../build/reference/entry-entry-point-symbol.md) do określenia punktu wejścia (funkcja) w programie. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe**stronę właściwości.

1. Wybierz **Ignoruj wszystkie domyślne biblioteki** właściwości lub określ listę bibliotek, aby zignorować w **Ignoruj określoną bibliotekę** właściwości. **Wiersza polecenia** właściwości strony wyświetli wpływu zmian do tych właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)