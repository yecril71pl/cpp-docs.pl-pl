---
title: /FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818625"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)

Przygotowuje obraz do poprawiania w trakcie działania.

## <a name="syntax"></a>Składnia

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>Argumenty

*space*<br/>
Wielkość uzupełnienia do dodania na początku każdej funkcji w bajtach. Na x86 to wartość domyślna to 5 bajtów uzupełnienia i na x64 to wartość domyślna to 6 bajtów. Wartość musi być podana dla innych elementów docelowych.

## <a name="remarks"></a>Uwagi

Aby konsolidator generuje obraz hotpatchable, pliki .obj muszą być skompilowane przy użyciu [/hotpatch (Utwórz obraz Hotpatchable)](hotpatch-create-hotpatchable-image.md).

Gdy kompilujesz i łączysz obraz za pomocą jednego wywołanie cl.exe, **/hotpatch** oznacza **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/FUNCTIONPADMIN** opcji **dodatkowe opcje**. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
