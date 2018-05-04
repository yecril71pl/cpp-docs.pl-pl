---
title: / FUNCTIONPADMIN (Utwórz obraz możliwych) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d0a5ecfcc336e198de0adcc2393f740072d70cae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)

Przygotowuje obraz do poprawiania w trakcie działania.

## <a name="syntax"></a>Składnia

> **/ FUNCTIONPADMIN**[**:**_miejsca_]  

### <a name="arguments"></a>Argumenty

*Miejsca*<br/>
Wielkość uzupełnienia do dodania na początku każdej funkcji w bajtach. Na x86 domyślnie 5 bajtów uzupełnienia i na x64 domyślnie do 6 bajtów. Należy podać wartość dla innych elementów docelowych.

## <a name="remarks"></a>Uwagi

Aby konsolidator, aby utworzyć obraz możliwych, pliki .obj musi zostały skompilowane z [/hotpatch (Utwórz obraz możliwych)](../../build/reference/hotpatch-create-hotpatchable-image.md).

Podczas kompilowania i połączyć obrazu z jednego wywołania cl.exe, **/hotpatch** oznacza **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wprowadź **/FUNCTIONPADMIN** opcji **dodatkowe opcje**. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
