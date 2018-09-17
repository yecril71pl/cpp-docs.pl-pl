---
title: -DELAYLOAD (Opóźnij importowanie ładowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 800b3d7d588d1038ac61cb7c9c4b9f1913bec9d4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722374"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Opóźnij importowanie ładowania)

> **/ DELAYLOAD:**_nazwa_pliku_dll_

## <a name="parameters"></a>Parametry

*Parametr DllName*<br/>
Nazwa biblioteki DLL, która ma opóźnić obciążenie.

## <a name="remarks"></a>Uwagi

Opcja/delayload powoduje, że biblioteka DLL, która jest określona przez `dllname` , należy załadować tylko przy pierwszym wywołaniu przez program do funkcji w tej bibliotece DLL. Aby uzyskać więcej informacji, zobacz [Obsługa konsolidatora dla bibliotek DLL Delay-Loaded](../../build/reference/linker-support-for-delay-loaded-dlls.md). Tę opcję wiele razy umożliwia określenie dowolnej liczby bibliotek DLL, wybierz polecenie. Musisz użyć Delayimp.lib. podczas połączenia programu lub możesz zaimplementować własną funkcję pomocnika obciążenia opóźnienia.

[/Opóźnienie](../../build/reference/delay-delay-load-import-settings.md) opcja Określa wiązanie i ładowania opcji dla każdej biblioteki DLL ładowanych z opóźnieniem.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

2. W **konsolidatora** folderu, wybierz **dane wejściowe** stronę właściwości.

3. Modyfikowanie **bibliotek DLL załadowanych z opóźnieniem** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)