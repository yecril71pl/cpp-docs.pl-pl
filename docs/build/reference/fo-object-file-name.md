---
title: -Fo (nazwa pliku obiektu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9ab671cbae276796ce89ec12cecbc16334e234e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724262"
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

[Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)