---
title: -V (numer wersji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ad42a72a874537a6307cfc547852f812f4aaaa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707970"
---
# <a name="v-version-number"></a>/V (Numer wersji)

Przestarzałe. Osadza ciąg tekstowy w pliku .obj.

## <a name="syntax"></a>Składnia

```
/Vstring
```

## <a name="arguments"></a>Argumenty

*string*<br/>
Ciąg określający osadzone w pliku .obj numer wersji lub informacje o prawach autorskich.

## <a name="remarks"></a>Uwagi

Etykieta stringcan pliku .obj, za pomocą numeru wersji lub informacje o prawach autorskich. Wszystkie znaki spacji lub tabulatorów muszą być ujęte w podwójny cudzysłów ("), jeśli są one częścią ciągu. Ukośnik odwrotny (\\) musi poprzedzać wszystkie znaki cudzysłowu, jeśli są one częścią ciągu. Odstęp między **/V** i `string` jest opcjonalne.

Można również użyć [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md) z argumentem typu komentarza kompilator umieszcza nazwę oraz numer wersji kompilatora w pliku .obj.

**/V** opcja jest przestarzały, począwszy od programu Visual Studio 2005; **/V** był głównie używane do obsługi tworzenia sterowniki urządzeń wirtualnych (urządzenia vxd) i tworzenia urządzenia vxd nie jest już obsługiwany przez zestaw narzędzi Visual C++. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

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