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
ms.openlocfilehash: 5e6302d90647bce7e37c47a619e814cab300aaee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319983"
---
# <a name="p-preprocess-to-a-file"></a>/P (Przetwarzaj wstępnie do pliku)

Wstępnie przetwarza pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.

## <a name="syntax"></a>Składnia

```
/P
```

## <a name="remarks"></a>Uwagi

Plik ma taką samą nazwę pliku źródłowego oraz rozszerzenie .i. W procesie przeprowadzane są wszystkie dyrektywy preprocesora, makra rozszerzenia są wykonywane i komentarze są usuwane. Aby zachować komentarzy w wstępnie przetworzone produkty wyjściowe, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](c-preserve-comments-during-preprocessing.md) wraz z opcją **/P**.

**/P** dodaje `#line` dyrektywy dane wyjściowe na początku i na końcu każdego dołączony plik i wokół wierszy usuniętych przez dyrektywy preprocesora dla kompilacji warunkowej. Te dyrektywy numerowania wierszy wstępnie przetworzonego pliku. W rezultacie wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy oryginalnego pliku źródłowego, a nie wiersze z wstępnie przetworzonego pliku. Aby pominąć Generowanie `#line` użyć dyrektyw, [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) także **/P**.

**/P** opcja pomija kompilację. Nie generuje pliku .obj, nawet w przypadku używania [/Fo (nazwa pliku obiektu)](fo-object-file-name.md). Należy ponownie przesłać wstępnie przetworzony plik dla kompilacji. **/P** powoduje również pominięcie pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

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

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](fi-preprocess-output-file-name.md)
