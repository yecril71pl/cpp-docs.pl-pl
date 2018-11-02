---
title: /Fm (Nazwa Mapfile)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: 49a3d20aee54b06bae2670be139d748fd2aaca6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469861"
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