---
title: /GZ (Włącz sprawdzanie błędów czasu wykonywania ramki stosu)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 3e6ffce487cc8183e45f3a911e7060ea22b28216
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810500"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Włącz sprawdzanie błędów czasu wykonywania ramki stosu)

Wykonuje te same operacje co [usunęliśmy (kontrole błąd czasu wykonywania)](rtc-run-time-error-checks.md) opcji. Przestarzałe.

## <a name="syntax"></a>Składnia

```
/GZ
```

## <a name="remarks"></a>Uwagi

**/GZ** jest tylko do użytku w nonoptimized ([/Od (Wyłącz (Debuguj))](od-disable-debug.md)) kompilacji.

**/GZ** jest przestarzała począwszy od programu Visual Studio 2005; użyj [usunęliśmy (kontrole błąd czasu wykonywania)](rtc-run-time-error-checks.md) zamiast tego. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
