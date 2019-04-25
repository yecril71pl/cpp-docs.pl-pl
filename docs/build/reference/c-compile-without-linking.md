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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294853"
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

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
