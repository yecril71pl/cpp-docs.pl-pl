---
title: /FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: c1e84f308796eabcaea61518e3731f633c2f67e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474896"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)

Przygotowuje obraz do poprawiania w trakcie działania.

## <a name="syntax"></a>Składnia

> **/ FUNCTIONPADMIN**[**:**_miejsca_]

### <a name="arguments"></a>Argumenty

*miejsce*<br/>
Wielkość uzupełnienia do dodania na początku każdej funkcji w bajtach. Na x86 to wartość domyślna to 5 bajtów uzupełnienia i na x64 to wartość domyślna to 6 bajtów. Wartość musi być podana dla innych elementów docelowych.

## <a name="remarks"></a>Uwagi

Aby konsolidator generuje obraz hotpatchable, pliki .obj muszą być skompilowane przy użyciu [/hotpatch (Utwórz obraz Hotpatchable)](../../build/reference/hotpatch-create-hotpatchable-image.md).

Gdy kompilujesz i łączysz obraz za pomocą jednego wywołanie cl.exe, **/hotpatch** oznacza **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/FUNCTIONPADMIN** opcji **dodatkowe opcje**. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
