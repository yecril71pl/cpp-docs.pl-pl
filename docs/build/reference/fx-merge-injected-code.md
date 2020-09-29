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
ms.openlocfilehash: b928ca63171f0f6d28859d049a1ed5008b908686
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500099"
---
# <a name="fx-merge-injected-code"></a>/Fx (Scalaj wprowadzony kod)

Tworzy kopię każdego pliku źródłowego z wstrzykniętym kodem scalonym ze źródłem.

## <a name="syntax"></a>Składnia

```
/Fx
```

## <a name="remarks"></a>Uwagi

Aby odróżnić scalony plik źródłowy od oryginalnego pliku źródłowego, **/FX** dodaje rozszerzenie. MRG między nazwą pliku a rozszerzeniem pliku. Na przykład plik o nazwie Moja Code. cpp zawierający kod z atrybutem i utworzony za pomocą **/FX** tworzy plik o nazwie MRG. cpp zawierający następujący kod:

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

W pliku. MRG kod, który został wstrzyknięty ze względu na atrybut, zostanie rozdzielony w następujący sposób:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

Atrybut [No_injected_text](../../windows/attributes/no-injected-text.md) jest osadzony w pliku. MRG, który umożliwia Kompilowanie pliku. MRG bez odwstrzykiwania tekstu.

Należy pamiętać, że plik źródłowy. MRG jest przeznaczony do reprezentowania kodu źródłowego wstrzykiwanego przez kompilator. Plik. MRG może nie kompilować ani działać dokładnie jako oryginalny plik źródłowy.

Makra nie są rozwinięte w pliku. MRG.

Jeśli program zawiera plik nagłówka, który używa wstrzykniętego kodu, **/FX** generuje plik. MRG. h dla tego nagłówka. **/FX** nie scala plików dołączanych, które nie używają wstrzykniętego kodu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++** .

1. Kliknij stronę właściwości **pliki wyjściowe** .

1. Zmodyfikuj właściwość **rozszerzonego atrybutu Source** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje pliku wyjściowego (/F)](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
