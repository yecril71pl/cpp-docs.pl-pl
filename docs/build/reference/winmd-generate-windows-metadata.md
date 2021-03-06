---
title: /WINMD (generuj metadane systemu Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 45d6492c87b7543a54d031f02dcf09e319150131
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449734"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generuj metadane systemu Windows)

Umożliwia generowanie pliku metadanych środowiska wykonawczego Windows (winmd).

> **/ WINMD**\[ **:** {**NIE**\|**TYLKO**}]

## <a name="arguments"></a>Argumenty

**/ WINMD**<br/>
Ustawieniem domyślnym dla aplikacji Universal Windows Platform. Konsolidator generuje binarny plik wykonywalny i pliku metadanych .winmd.

**/WINMD:NO**<br/>
Konsolidator wygeneruje tylko binarny plik wykonywalny, ale nie w pliku winmd.

**/ WINMD: TYLKO**<br/>
Konsolidator generuje plik .winmd, ale nie binarny plik wykonywalny.

## <a name="remarks"></a>Uwagi

**/WINMD** — opcja konsolidatora służy do kontrolowania utworzenie pliku metadanych (.winmd) środowiska uruchomieniowego Windows dla aplikacji platformy uniwersalnej systemu Windows i składników środowiska wykonawczego Windows. Plik .winmd jest rodzajem biblioteki dll, który zawiera metadane dla typów środowiska wykonawczego Windows, a w przypadku składników środowiska wykonawczego, implementacji tych typów. Metadane następuje [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm) standardowych.

Domyślnie, nazwa pliku wyjściowego ma postać *binaryname*winmd. Aby określić inną nazwę pliku, użyj [/winmdfile](winmdfile-specify-winmd-file.md) opcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **metadanych Windows** stronę właściwości.

1. W **Generowanie metadanych Windows** listy rozwijanej wybierz odpowiednią opcję.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Tworzenie składnika proste Windows Runtime i wywoływanie z kodu JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Wprowadzenie do języka definicji interfejsu Microsoft 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (Określ plik winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (Określ plik klucza winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (Określ kontener klucza)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (Podpisz częściowo winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
