---
title: "-DRIVER (sterownik trybu jądra systemu Windows NT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs: C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29234e3c0e368c7710f9071c753422bc4e6ef2b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Sterownik trybu jądra Windows NT)

>/ DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>Uwagi

Użyj **/Driver** — opcja konsolidatora do tworzenia sterownik trybu jądra systemu Windows NT.

**/DRIVER:UPONLY** powoduje, że konsolidator dodać **IMAGE_FILE_UP_SYSTEM_ONLY** bit do charakterystyki w nagłówku wyjściowym, aby określić, że jest jednoprocesorowy (UP) sterowników. System operacyjny będzie odmawiał załadowania sterownika JEDNOPROCESOROWEGO w systemie wieloprocesorowym (MP).

**/ Driver: WDM** powoduje, że konsolidator ustawia **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** bitu w polu opcjonalne nagłówka DllCharacteristics.

Jeśli **/Driver** nie zostanie określony, te usługi bits nie są skonfigurowane przez konsolidator.

Jeśli **/Driver** określono:

- **/ Fixed: No** jest włączona. Aby uzyskać więcej informacji, zobacz [Fixed (stałe adresu podstawowego)](../../build/reference/fixed-fixed-base-address.md).

- Rozszerzenie pliku wyjściowego jest ustawiony na .sys. Użyj **/OUT** zmienić domyślną nazwę pliku i rozszerzenia. Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** strony właściwości.

1. Modyfikowanie **sterownika** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz [VCLinkerTool.driver właściwości](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)
