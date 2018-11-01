---
title: /WINMD (generuj metadane systemu Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 3a59dd770d9429f23a4f401c6e1f5b13b9f743ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656108"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generuj metadane systemu Windows)

Umożliwia generowanie pliku metadanych środowiska wykonawczego Windows (winmd).

> **/ WINMD**\[**:**{**NIE**\|**TYLKO**}]

## <a name="arguments"></a>Argumenty

**/ WINMD**<br/>
Ustawieniem domyślnym dla aplikacji Universal Windows Platform. Konsolidator generuje binarny plik wykonywalny i pliku metadanych .winmd.

**/WINMD:NO**<br/>
Konsolidator wygeneruje tylko binarny plik wykonywalny, ale nie w pliku winmd.

**/ WINMD: TYLKO**<br/>
Konsolidator generuje plik .winmd, ale nie binarny plik wykonywalny.

## <a name="remarks"></a>Uwagi

**/WINMD** — opcja konsolidatora służy do kontrolowania utworzenie pliku metadanych (.winmd) środowiska uruchomieniowego Windows dla aplikacji platformy uniwersalnej systemu Windows i składników środowiska wykonawczego Windows. Plik .winmd jest rodzajem biblioteki dll, który zawiera metadane dla typów środowiska wykonawczego Windows, a w przypadku składników środowiska wykonawczego, implementacji tych typów. Metadane następuje [ECMA-335](http://www.ecma-international.org/publications/standards/Ecma-335.htm) standardowych.

Domyślnie, nazwa pliku wyjściowego ma postać *binaryname*winmd. Aby określić inną nazwę pliku, użyj [/winmdfile](../../build/reference/winmdfile-specify-winmd-file.md) opcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **metadanych Windows** stronę właściwości.

1. W **Generowanie metadanych Windows** listy rozwijanej wybierz odpowiednią opcję.

## <a name="see-also"></a>Zobacz też

[Wskazówki: Tworzenie składnika proste Windows Runtime i wywoływania go z kodu JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Wprowadzenie do języka definicji interfejsu Microsoft 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (Określ plik winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (Określ plik klucza winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (Określ kontener klucza)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (Podpisz częściowo winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
