---
title: / FUNCTIONPADMIN (Utwórz obraz Hotpatchable) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a82611c453a96e9247e414d6adb777c07320482
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703992"
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
