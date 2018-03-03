---
title: -Zo (Rozszerzanie zoptymalizowanego debugowania) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 326bd1c6c435dec97c309014dfc81ca444cc5eb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (rozszerzanie zoptymalizowanego debugowania)
Generowanie rozszerzone informacje debugowania zoptymalizowanego kodu w kompilacji bez debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
/Zo[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/Zo** przełącznik kompilator generuje rozszerzone informacje debugowania zoptymalizowanego kodu. Optymalizacja może rejestrów dla zmiennych lokalnych, zmienianie kolejności kodu, vectorize pętli i wywołania funkcji wbudowanej. Te optymalizacje mogą przesłaniać relacji między kodu źródłowego i kod skompilowany obiekt. **/Zo** przełącznika informuje kompilator, aby wygenerować dodatkowe informacje o debugowaniu dla zmiennych lokalnych i funkcji śródwierszowych. Użyj go, aby wyświetlić zmiennych w **automatycznych**, **zmiennych lokalnych**, i **czujki** systemu windows, gdy kroków opisanych w zoptymalizowanego kodu w debugerze programu Visual Studio. Umożliwia również ślady stosu pokazać funkcje wbudowane w debugerze WinDBG. Debugowanie kompilacji, które zostało wyłączone optymalizacje ([/Od](../../build/reference/od-disable-debug.md)) nie są dodatkowe informacje o debugowaniu, generowane podczas **/Zo** jest określona. Użyj **/Zo** przełącznika do debugowania z optymalizacją włączone konfiguracje wersji. Aby uzyskać więcej informacji na optymalizacji przełączników, zobacz [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md). **/Zo** opcja jest włączona domyślnie w programie Visual Studio po określeniu informacji o debugowaniu z **/zi** lub **/z7**. Określ **/Zo-** jawnie wyłączyć tę opcję kompilatora.  
  
 **/Zo** jest dostępny w programie Visual Studio 2013 Update 3 i zastępuje go wcześniej nieudokumentowanej **/d2Zi+** przełącznika.  
  
### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Aby ustawić /Zo — opcja kompilatora w programie Visual Studio  
  
1.  Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji**, **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić `/Zo` , a następnie wybierz **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)   
 [/ Z7, / zi, /ZI (Format informacji o debugowaniu)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue)