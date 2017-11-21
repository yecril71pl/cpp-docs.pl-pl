---
title: "-E (wstępnie Przetwórz do stdout) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /e
dev_langs: C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3540a2d6d1c32a72d16cdb9bdab19aa18604021
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="e-preprocess-to-stdout"></a>/E (Przetwarzaj wstępnie do stdout)
Przetwarza wstępnie pliki źródłowe C i C++ i kopiuje wstępnie przetworzonych plików na urządzeniu standardowe dane wyjściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/E  
```  
  
## <a name="remarks"></a>Uwagi  
 W tym procesie nie zostaną przeprowadzone wszystkie dyrektywy preprocesora, rozwinięcia makra są są wykonywane i komentarze zostaną usunięte. Aby zachować komentarzy w wstępnie przetworzonych danych wyjściowych, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) również — opcja kompilatora.  
  
 **/E** dodaje `#line` dyrektywy dane wyjściowe na początku i na końcu każdej dołączanego pliku i wokół wierszy usunięte przez dyrektywy preprocesora dla kompilacji warunkowej. Te dyrektywy numerowania wierszy wstępnie przetworzonych plików. W związku z tym wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy oryginalnego pliku źródłowego, a nie wierszy w pliku wstępnie przetworzony.  
  
 **/E** opcja pomija kompilację. Należy ponownie przesłać wstępnie przetworzonych plików dla kompilacji. **/E** również pomija pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
 Aby pominąć `#line` użyj dyrektywy, [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) zamiast tego należy.  
  
 Aby wysłać wstępnie przetworzone produkty wyjściowe do pliku, nie do `stdout`, użyj [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) zamiast tego należy.  
  
 Aby pominąć `#line` dyrektywy i wysyłanie wstępnie przetworzone produkty wyjściowe do pliku, użyj **/P** i **/EP** ze sobą.  
  
 Nie można użyć prekompilowanych nagłówków z **/E** opcji.  
  
 Należy pamiętać, że podczas przetwarzania wstępnego do osobnego pliku, spacje nie są emitowane po tokenów. Może to spowodować programu niedozwolony lub mieć niezamierzone skutki uboczne. Następujący program kompiluje pomyślnie:  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 Jednak jeśli kompilacji z:  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 `int main`w test2.cpp niepoprawnie będzie `intmain`.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje**pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Przykład  
 Przetwarza wstępnie następujące polecenie w wierszu `ADD.C`, zachowuje komentarze, dodaje `#line` dyrektywy i wyświetla wyniki na urządzeniu standardowe dane wyjściowe:  
  
```  
CL /E /C ADD.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)