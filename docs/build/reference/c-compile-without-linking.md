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
ms.openlocfilehash: bfe351daf43b913f10df74b1059ba98f7d5d657b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815167"
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

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
