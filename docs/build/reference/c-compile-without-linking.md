---
title: /c (Kompiluj bez konsolidacji)
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: 6be3b15efb56e97d658edb5890c3bdce4f64fbd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625163"
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