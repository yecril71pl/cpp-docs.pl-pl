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
ms.openlocfilehash: a8f2c1a196f18e6d310fd41d4dbed751440a4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293046"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

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

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
