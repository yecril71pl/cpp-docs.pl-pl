---
title: -showIncludes (Wymień pliki dołączane) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51305212f97482c6963ee2ba0d272c5c4692416e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709398"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (Wymień pliki dołączane)

Powoduje, że kompilator danych wyjściowych listy plików dołączanych. Zagnieżdżone obejmują pliki są również wyświetlane (plikami dołączonymi z plików, które należy uwzględnić).

## <a name="syntax"></a>Składnia

```
/showIncludes
```

## <a name="remarks"></a>Uwagi

W przypadku pliku dołączanego podczas kompilacji wiadomość jest na przykład danych wyjściowych:

```
Note: including file: d:\MyDir\include\stdio.h
```

Zagnieżdżone obejmują pliki są wskazywane przez wcięcia jedno miejsce dla poszczególnych poziomów zagnieżdżenia, na przykład:

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

W tym przypadku `2.h` został dostarczony z w ramach `1.h`, dlatego wcięcia.

**/Showincludes** opcji emituje do `stderr`, a nie `stdout`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Pokaż obejmuje** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)