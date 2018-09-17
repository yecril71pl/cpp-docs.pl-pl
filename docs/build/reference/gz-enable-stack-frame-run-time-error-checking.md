---
title: -GZ (Włącz stosu sprawdzanie błędów czasu wykonywania ramki) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gz
dev_langs:
- C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f13824064b7c7dcdb75524a22b14a4d90942918
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707229"
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