---
title: /NODEFAULTLIB (Ignoruj biblioteki)
ms.date: 03/26/2019
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
ms.openlocfilehash: 24528eb4c387c4cd0921ab089370d72b076ad640
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508757"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignoruj biblioteki)

> **/ NODEFAULTLIB**[__:__*biblioteki*]

## <a name="arguments"></a>Argumenty

*Biblioteka*<br/>
Biblioteka, która ma konsolidator, aby ignorować podczas rozpoznawania odwołań zewnętrznych.

## <a name="remarks"></a>Uwagi

Opcja/nodefaultlib informuje konsolidator, aby usunąć co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.

Aby utworzyć pliku .obj, który nie zawiera żadnych odwołań do bibliotek domyślnych, użyj [/Zl (Pomiń domyślną nazwę biblioteki)](zl-omit-default-library-name.md).

Domyślnie/nodefaultlib usuwa wszystkie domyślne biblioteki z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. Opcjonalny *biblioteki* parametr umożliwia usunięcie określonej biblioteki z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych. Określ jedną z opcji/nodefaultlib bibliotek, które chcesz wykluczyć.

Konsolidator usuwa odwołań na definicje zewnętrzne, wyszukując najpierw w bibliotekach, które zostaną jawnie określone, a następnie w domyślnych bibliotek określony za pomocą [/DEFAULTLIB:](defaultlib-specify-default-library.md) opcji, a następnie, w domyślnym biblioteki o nazwie w .obj pliki.

/ NODEFAULTLIB:*biblioteki* zastępuje /DEFAULTLIB:*biblioteki* gdy takie same *biblioteki* nazwa jest określona w obu.

Użycie opcji/nodefaultlib do budowania programu bez biblioteki wykonawczej języka C, należy również użyć [/Entry](entry-entry-point-symbol.md) Aby określić funkcję punktu wejścia programu. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **dane wejściowe** stronę właściwości.

1. Wybierz **Ignoruj wszystkie domyślne biblioteki** właściwości. Lub określ rozdzieloną średnikami listę bibliotek, aby zignorować w **Ignoruj określone biblioteki domyślne** właściwości. **Wiersza polecenia** strona właściwości pokazuje wpływ zmian do tych właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
