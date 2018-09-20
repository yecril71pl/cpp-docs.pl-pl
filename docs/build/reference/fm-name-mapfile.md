---
title: -Fm (nazwa Mapfile) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fm
dev_langs:
- C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bce549cd782c8d79066b16d2e3791ba906e9c4f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410538"
---
# <a name="fm-name-mapfile"></a>/Fm (Nazwa Mapfile)

Informuje konsolidator, aby wygenerować plik mapy zawierającego listę segmentów w kolejności, w jakiej występują w odpowiedniego pliku .exe lub DLL.

## <a name="syntax"></a>Składnia

```
/Fmpathname
```

## <a name="remarks"></a>Uwagi

Domyślnie pliku mapfile znajduje się odpowiedni plik źródłowy C lub C++ z podstawowej nazwy. Rozszerzenie mapowania.

Określanie **/Fm** ma ten sam efekt, tak, jakby była określona [/map (Generuj plik mapy)](../../build/reference/map-generate-mapfile.md) — opcja konsolidatora.

Jeśli określisz [/c (Kompiluj bez konsolidacji)](../../build/reference/c-compile-without-linking.md) do pomijania, łączenie, **/Fm** nie ma wpływu.

Symbole globalne w pliku mapowania zazwyczaj mają co najmniej jeden wiodące znaki podkreślenia, ponieważ kompilator sam doda do nazwy zmiennych wiodącego podkreślenia. Wiele symbole globalne, które pojawiają się w pliku mapfile są używane wewnętrznie przez kompilator i standardowych bibliotek.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)