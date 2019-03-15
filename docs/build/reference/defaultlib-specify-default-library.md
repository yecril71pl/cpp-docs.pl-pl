---
title: /DEFAULTLIB (Określ bibliotekę domyślną)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 0b7d4569c7be70bd97094ebbe09a7ae462331983
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815960"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Określ bibliotekę domyślną)

Określ bibliotekę domyślną do przeszukania w celu rozpoznawania odwołań zewnętrznych.

## <a name="syntax"></a>Składnia

> **/ DEFAULTLIB**:_biblioteki_

### <a name="arguments"></a>Argumenty

*Biblioteka*<br/>
Nazwa biblioteki wyszukiwania podczas rozpoznawania odwołań zewnętrznych.

## <a name="remarks"></a>Uwagi

**/DEFAULTLIB** opcja dodaje jeden *biblioteki* listę bibliotek, które łączy wyszukiwania podczas rozpoznawania odwołań. Określony za pomocą biblioteki **/DEFAULTLIB** przeszukiwany jest po biblioteki określone jawnie w wierszu polecenia i przed domyślne biblioteki o nazwie w plikach .obj.

Gdy jest używana bez argumentów, [/nodefaultlib (Ignoruj wszystkie domyślne biblioteki)](nodefaultlib-ignore-libraries.md) opcja przesłania wszystkie **/DEFAULTLIB**:*biblioteki* opcje. **/Nodefaultlib**:*biblioteki* opcję zastąpienia **/DEFAULTLIB**:*biblioteki* gdy takie same *biblioteki*nazwa jest określona w obu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje**, wprowadź **/DEFAULTLIB**:*biblioteki* opcję dla każdej biblioteki do wyszukania. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
