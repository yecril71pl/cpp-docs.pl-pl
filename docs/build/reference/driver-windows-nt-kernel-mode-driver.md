---
title: -DRIVER (sterownik trybu jądra Windows NT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ae096c502cdc94d47a516caf4c29ac4f3eceb4b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705552"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Sterownik trybu jądra Windows NT)

>/ DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>Uwagi

Użyj **Driver/Driver** — opcja konsolidatora do tworzenia sterownik trybu jądra Windows NT.

**/DRIVER:UPONLY** powoduje, że konsolidator dodaje **IMAGE_FILE_UP_SYSTEM_ONLY** bit do charakterystyki w nagłówku wyjściowym, aby określić, że jest ona jednoprocesorowy (UP) sterownika. System operacyjny będzie odmawiał załadowania sterownika JEDNOPROCESOROWEGO w systemie wieloprocesorowym (MP).

**WDM** powoduje, że konsolidator ustawia **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** bit w dllcharacteristics w opcjonalnym nagłówku.

Jeśli **Driver/Driver** nie zostanie określony, bity te nie są ustawione przez konsolidator.

Jeśli **Driver/Driver** określono:

- **/ Fixed: No** jest aktywna. Aby uzyskać więcej informacji, zobacz [/Fixed (stały adres podstawowy)](../../build/reference/fixed-fixed-base-address.md).

- Rozszerzenie nazwy pliku wyjściowego jest równa .sys. Użyj **/OUT** zmienić domyślną nazwę pliku i rozszerzenie. Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Modyfikowanie **sterownika** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz [właściwość VCLinkerTool.driver](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
