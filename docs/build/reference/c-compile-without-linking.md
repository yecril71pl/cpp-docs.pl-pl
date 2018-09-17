---
title: -c (Kompiluj bez konsolidacji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de6fe291bde8652b772c7091c1919836f88960fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710349"
---
# <a name="c-compile-without-linking"></a>/c (Kompiluj bez konsolidacji)

Uniemożliwia automatyczne wywołanie do łącza.

## <a name="syntax"></a>Składnia

```
/c
```

## <a name="remarks"></a>Uwagi

Kompilowanie przy użyciu **/c** tworzy tylko pliki .obj. ŁĄCZE musi jawnie wywołać z opcjami do wykonywania połączeń fazy kompilacji i odpowiednie pliki.

Wszelkie wewnętrzny projekt utworzony w środowisku programistycznym korzysta z **/c** opcja domyślnie.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

- Ta opcja nie jest dostępne z poziomu środowiska deweloperskiego.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Aby programowo ustawić tę opcję kompilatora, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu tworzy plików obiektów FIRST.obj i SECOND.obj. THIRD.obj jest ignorowany.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

Aby utworzyć plik wykonywalny, należy wywołać łącza:

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)