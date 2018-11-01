---
title: /P (Przetwarzaj wstępnie do pliku)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 9b3d84d94ed75acd68011b895afbc4f190019673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622245"
---
# <a name="p-preprocess-to-a-file"></a>/P (Przetwarzaj wstępnie do pliku)

Wstępnie przetwarza pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.

## <a name="syntax"></a>Składnia

```
/P
```

## <a name="remarks"></a>Uwagi

Plik ma taką samą nazwę pliku źródłowego oraz rozszerzenie .i. W procesie przeprowadzane są wszystkie dyrektywy preprocesora, makra rozszerzenia są wykonywane i komentarze są usuwane. Aby zachować komentarzy w wstępnie przetworzone produkty wyjściowe, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) wraz z opcją **/P**.

**/P** dodaje `#line` dyrektywy dane wyjściowe na początku i na końcu każdego dołączony plik i wokół wierszy usuniętych przez dyrektywy preprocesora dla kompilacji warunkowej. Te dyrektywy numerowania wierszy wstępnie przetworzonego pliku. W rezultacie wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy oryginalnego pliku źródłowego, a nie wiersze z wstępnie przetworzonego pliku. Aby pominąć Generowanie `#line` użyć dyrektyw, [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) także **/P**.

**/P** opcja pomija kompilację. Nie generuje pliku .obj, nawet w przypadku używania [/Fo (nazwa pliku obiektu)](../../build/reference/fo-object-file-name.md). Należy ponownie przesłać wstępnie przetworzony plik dla kompilacji. **/P** powoduje również pominięcie pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **preprocesora** stronę właściwości.

1. Modyfikowanie **Generowanie wstępnie przetworzony plik** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu wstępnie przetwarza `ADD.C`, zachowuje komentarze, dodaje `#line` dyrektyw i zapisuje wynik w pliku `ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](../../build/reference/fi-preprocess-output-file-name.md)