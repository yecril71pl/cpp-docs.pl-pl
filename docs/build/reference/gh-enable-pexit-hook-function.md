---
title: "-GH (Włącz funkcję _pexit Hook) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _pexit
dev_langs: C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02cfdd783a698a3397e84fa62b7252399570dc84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Włącz funkcję _pexit Hook)
Wywołania `_pexit` funkcja na końcu każdej metody lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GH  
```  
  
## <a name="remarks"></a>Uwagi  
 `_pexit` Funkcja nie jest częścią żadnej biblioteki i jest maksymalnie o podanie definicji `_pexit`.  
  
 Jeśli nie chcesz jawnie wywołać `_pexit`, nie trzeba podać prototypu. Funkcja muszą znajdować się tak, jakby miała następujące prototypu, a i musi być wypychania zawartości wszystkich rejestrów na zapis pop zawartości bez zmian na wyjściu:  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit`przypomina `_penter`; zobacz [/Gh (Włącz _penter Hook funkcji)](../../build/reference/gh-enable-penter-hook-function.md) przykład sposobu pisania `_pexit` funkcji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)