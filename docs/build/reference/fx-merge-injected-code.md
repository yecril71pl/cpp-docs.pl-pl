---
title: /Fx (Scalaj wprowadzony kod)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: f1a266eee4edc524fbbe49bdef31a8235f62bd3c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818144"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **rozwiń źródła opartego na atrybutach** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
