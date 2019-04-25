---
title: /DELAYLOAD (Opóźnij importowanie ładowania)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: e92b470b7b5e76b39371f333cbbda150e7f6e8c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273362"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Opóźnij importowanie ładowania)

> **/ DELAYLOAD:**_nazwa_pliku_dll_

## <a name="parameters"></a>Parametry

*dllname*<br/>
Nazwa biblioteki DLL, która ma opóźnić obciążenie.

## <a name="remarks"></a>Uwagi

Opcja/delayload powoduje, że biblioteka DLL, która jest określona przez `dllname` , należy załadować tylko przy pierwszym wywołaniu przez program do funkcji w tej bibliotece DLL. Aby uzyskać więcej informacji, zobacz [Obsługa konsolidatora dla bibliotek DLL Delay-Loaded](linker-support-for-delay-loaded-dlls.md). Tę opcję wiele razy umożliwia określenie dowolnej liczby bibliotek DLL, wybierz polecenie. Musisz użyć Delayimp.lib. podczas połączenia programu lub możesz zaimplementować własną funkcję pomocnika obciążenia opóźnienia.

[/Opóźnienie](delay-delay-load-import-settings.md) opcja Określa wiązanie i ładowania opcji dla każdej biblioteki DLL ładowanych z opóźnieniem.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W **konsolidatora** folderu, wybierz **dane wejściowe** stronę właściwości.

1. Modyfikowanie **bibliotek DLL załadowanych z opóźnieniem** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
