---
title: -E (Przetwarzaj wstępnie do stdout) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /e
dev_langs:
- C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48517f4469f203f5e29fbaa4ec105a3e36aafb44
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720274"
---
# <a name="e-preprocess-to-stdout"></a>/E (Przetwarzaj wstępnie do stdout)

Wstępnie przetwarza pliki źródłowe C i C++ i kopiuje pliki wstępnie przetworzony do urządzenia wyjścia standardowego.

## <a name="syntax"></a>Składnia

```
/E
```

## <a name="remarks"></a>Uwagi

W ramach tego procesu są przeprowadzane wszystkie dyrektywy preprocesora, makra rozszerzenia są wykonywane i komentarze są usuwane. Aby zachować komentarzy w wstępnie przetworzone produkty wyjściowe, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) również opcję kompilatora.

**/E** dodaje `#line` dyrektywy danych wyjściowych na początku i końcu każdego dołączony plik i wokół wierszy usuniętych przez dyrektywy preprocesora dla kompilacji warunkowej. Te dyrektywy numerowania wierszy wstępnie przetworzonego pliku. W rezultacie wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy oryginalnego pliku źródłowego, a nie wiersze z wstępnie przetworzonego pliku.

**/E** opcja pomija kompilację. Należy ponownie przesłać wstępnie przetworzony plik dla kompilacji. **/E** powoduje również pominięcie pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).

Aby pominąć `#line` użyć dyrektyw, [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) zamiast opcji.

Aby wysłać wstępnie przetworzone produkty wyjściowe do pliku, nie do `stdout`, użyj [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) zamiast opcji.

Aby pominąć `#line` dyrektywy i wysyłanie wstępnie przetworzone produkty wyjściowe do pliku, użyj **/P** i **/EP** ze sobą.

Nie można użyć wstępnie skompilowanych nagłówków z **/E** opcji.

Należy pamiętać, że podczas przetwarzania wstępnego w oddzielnym pliku, spacje nie są emitowane po tokenów. To spowodować niedozwolony program, lub mieć niezamierzone efekty uboczne. Następujący program kompiluje się pomyślnie:

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

Jednakże jeśli kompilujesz z opcją:

```
cl -E test.cpp > test2.cpp
```

`int main` w test2.cpp niepoprawnie będzie `intmain`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje**pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu wstępnie przetwarza `ADD.C`, zachowuje komentarze, dodaje `#line` dyrektyw i wyświetla wynik na urządzeniu standardowe dane wyjściowe:

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)