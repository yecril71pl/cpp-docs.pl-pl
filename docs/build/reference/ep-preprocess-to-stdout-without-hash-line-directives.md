---
title: '-EP (wstępnie Przetwórz do stdout bez dyrektyw #line) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598c202cbac0176cb77243c7f0f891ef94c3dcc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714886"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Wstępnie przetwórz do stdout bez dyrektyw #line)

Wstępnie przetwarza pliki źródłowe C i C++ i kopiuje pliki wstępnie przetworzony do urządzenia wyjścia standardowego.

## <a name="syntax"></a>Składnia

```
/EP
```

## <a name="remarks"></a>Uwagi

W procesie przeprowadzane są wszystkie dyrektywy preprocesora, makra rozszerzenia są wykonywane i komentarze są usuwane. Aby zachować komentarzy w wstępnie przetworzone produkty wyjściowe, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) z opcją **/EP**.

**/EP** opcja pomija kompilację. Należy ponownie przesłać wstępnie przetworzony plik dla kompilacji. **/EP** powoduje również pominięcie pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).

Wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy wstępnie przetworzony plik, a nie oryginalnego pliku źródłowego. Jeśli chcesz, aby numery wierszy do odwoływania się do oryginalnego pliku źródłowego, należy użyć [/E (Przetwarzaj wstępnie do stdout)](../../build/reference/e-preprocess-to-stdout.md) zamiast tego. **/E** opcja dodaje `#line` dyrektywy dane wyjściowe do tego celu.

Aby wysłać wstępnie przetworzone produkty wyjściowe z `#line` dyrektywy w pliku użyj [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) zamiast opcji.

Aby wysłać wstępnie przetworzone produkty wyjściowe do stdout, za pomocą `#line` użyć dyrektyw, **/P** i **/EP** ze sobą.

Nie można użyć wstępnie skompilowanych nagłówków z **/EP** opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **preprocesora** stronę właściwości.

1. Modyfikowanie **Generowanie wstępnie przetworzony plik** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu wstępnie przetwarza plik `ADD.C`zachowuje komentarze i wyświetla wynik na urządzeniu standardowe dane wyjściowe:

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)