---
title: -analyze (analiza kodu) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs: C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba76ddd10866e414d9817f628c7a1aec019964de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="analyze-code-analysis"></a>/analyze (analiza kodu)
Włącza opcje analizy kodu i kontroli.  
  
## <a name="syntax"></a>Składnia  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## <a name="arguments"></a>Argumenty  
 /analyze  
 Włącza funkcję analizy w trybie domyślnym. Analizy danych wyjściowych przechodzi do **dane wyjściowe** okna, podobnie jak inne komunikaty o błędach. Użyj **/ analyze-** jawnie wyłączyć analizy.  
  
 /analyze:WX-  
 Określanie **/ analyze: WX -** oznacza, że ostrzeżeń analizy kodu nie są traktowane jako błędy podczas kompilowania przy użyciu **wx**. Aby uzyskać więcej informacji, zobacz [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md).  
  
 / analyze: dziennika`filename`  
 Analizator szczegółowe wyniki są zapisywane jako XML do pliku określonego przez `filename`.  
  
 /analyze:quiet  
 Wyłącza dane wyjściowe analizatora do **dane wyjściowe** okna.  
  
 / analyze: stacksize`number`  
 `number` Parametr, który jest używany z tą opcją Określa rozmiar w bajtach ramki stosu dla ostrzeżenia, które [C6262](/visualstudio/code-quality/c6262) jest generowany. Jeśli ten parametr nie jest określony, rozmiar ramki stosu to domyślnie 16 KB.  
  
 / analyze: max_paths`number`  
 `number` Parametr, który jest używany z tą opcją określa maksymalną liczbę ścieżek kodu do analizy. Jeśli ten parametr nie jest określony, domyślna liczba to 256. Większe wartości wykonują bardziej szczegółowe sprawdzanie, ale analiza może zająć więcej czasu.  
  
 /analyze:only  
 Zazwyczaj po uruchomieniu analizatora kompilator generuje kod i wykonuje bardziej gruntowne sprawdzanie składni. **/ Analyze: tylko** opcja powoduje wyłączenie tego przebiegu generowania kodu; analizy dzięki temu szybsze, ale nie są emitowane kompilacji błędów i ostrzeżeń, które może być wykryte przez program przebiegu generowania kodu kompilator. Jeśli program nie jest wolny od błędów generowania kodu, wyniki analizy mogą być zawodne; dlatego zaleca się użycie tej opcji tylko wtedy, gdy kod już przechodzi sprawdzanie składni generowania kodu bez błędów.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [analizy kodu dla C/C++ — omówienie](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) i [analizy kodu dla C/C++ — ostrzeżenia](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **analizy kodu** węzła.  
  
4.  Wybierz **ogólne** strony właściwości.  
  
5.  Zmodyfikuj jedną lub więcej **analizy kodu** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)