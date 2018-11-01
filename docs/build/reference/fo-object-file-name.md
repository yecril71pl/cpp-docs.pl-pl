---
title: /Fo (Nazwa pliku obiektu)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: 19e84cbb1be53c8e1a7ae32b6ea2fc3ceeb2edae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640339"
---
# <a name="fo-object-file-name"></a>/Fo (Nazwa pliku obiektu)

Określa nazwę pliku obiektu (.obj) lub katalog ma być używany zamiast domyślnego.

## <a name="syntax"></a>Składnia

```
/Fopathname
```

## <a name="remarks"></a>Uwagi

Jeśli ta opcja nie zostanie użyta, korzysta z nazwa podstawowa pliku źródłowego i rozszerzeniem nazwy pliku obiektu. Można użyć dowolnej nazwy i rozszerzenie, które ma, ale Konwencji zalecane jest użycie. obiektu

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **nazwy pliku obiektu** właściwości.  W środowisku programistycznym pliku obiektu musi mieć rozszerzenie. obiektu

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie tworzy plik obiektu o nazwie THIS.obj w istniejącym katalogiem, \OBJECT, na dysku B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)