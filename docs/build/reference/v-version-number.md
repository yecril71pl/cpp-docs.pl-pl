---
title: /V (Numer wersji)
ms.date: 11/04/2016
f1_keywords:
- /v
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
ms.openlocfilehash: 7bebd3ab9677bb340203bbf857e4ee9f287e36e6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817611"
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

**/V** opcja jest przestarzały, począwszy od programu Visual Studio 2005; **/V** był głównie używane do obsługi tworzenia sterowniki urządzeń wirtualnych (urządzenia vxd) i tworzenia urządzenia vxd nie jest już obsługiwany przez zestaw narzędzi Visual C++. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

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
