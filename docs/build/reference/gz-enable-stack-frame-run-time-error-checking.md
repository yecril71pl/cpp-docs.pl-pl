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
ms.openlocfilehash: 86d9b2cb7da3c21ce46331d9f817911b65c4ba2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562902"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Włącz sprawdzanie błędów czasu wykonywania ramki stosu)

Wykonuje te same operacje co [usunęliśmy (kontrole błąd czasu wykonywania)](../../build/reference/rtc-run-time-error-checks.md) opcji. Przestarzałe.

## <a name="syntax"></a>Składnia

```
/GZ
```

## <a name="remarks"></a>Uwagi

**/GZ** jest tylko do użytku w nonoptimized ([/Od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md)) kompilacji.

**/GZ** jest przestarzała począwszy od programu Visual Studio 2005; użyj [usunęliśmy (kontrole błąd czasu wykonywania)](../../build/reference/rtc-run-time-error-checks.md) zamiast tego. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)