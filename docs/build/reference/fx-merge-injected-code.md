---
title: -Fx (Scalaj wprowadzony kod) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs:
- C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca8522f85a8ce10bc694ab1144e7f24ed3fca6fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425759"
---
# <a name="fx-merge-injected-code"></a>/Fx (Scalaj wprowadzony kod)

Tworzy kopię każdego pliku źródłowego z kodem scalane w źródle.

## <a name="syntax"></a>Składnia

```
/Fx
```

## <a name="remarks"></a>Uwagi

Aby rozróżnić pliku źródłowego scalone z oryginalnego pliku źródłowego **/Fx** dodanie rozszerzenia .mrg między nazwę pliku i rozszerzenie pliku. Na przykład plik o nazwie MyCode.cpp zawierające kod opartego na atrybutach i utworzonych za pomocą **/Fx** tworzy plik o nazwie MyCode.mrg.cpp zawierający następujący kod:

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

W pliku .mrg kod, który został wprowadzony ze względu na atrybut będzie rozdzielonych w następujący sposób:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

[No_injected_text](../../windows/no-injected-text.md) atrybutu jest osadzony w pliku .mrg, który umożliwia kompilacji pliku .mrg bez tekstu jest reinjected.

Należy pamiętać, że plik źródłowy .mrg ma być reprezentację kodu źródłowego, które są wstrzykiwane przez kompilator. Plik .mrg mogą kompilacji albo nie działać dokładnie jako oryginalnego pliku źródłowego.

Makra nie zostaną rozwinięte w pliku .mrg.

Jeśli program obejmuje pliku nagłówka, który używa wprowadzonego kodu **/Fx** generuje. mrg.h w pliku nagłówka. **/FX** scalania nie obejmuje pliki, które nie korzystają z kodem.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **rozwiń źródła opartego na atrybutach** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)