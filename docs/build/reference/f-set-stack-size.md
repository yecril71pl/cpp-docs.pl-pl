---
title: -F (Ustaw rozmiar stosu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed0ad03d18493cc5618f9aad2a16b07e4a01717f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="f-set-stack-size"></a>/F (Ustaw rozmiar stosu)
Ustawia rozmiar stosu program w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```  
/F number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Rozmiar stosu w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Bez tej opcji Rozmiar stosu domyślnie 1 MB. `number` Argument może być w wartości dziesiętne lub notacji języka C. Argument może wynosić od 1 do rozmiar maksymalny stosu zaakceptowane przez konsolidator. Konsolidator Zaokrągla wartość w górę określonej wartości najbliższej 4 bajty. Odstęp między **/F** i `number` jest opcjonalna.  
  
 Konieczne może być Zwiększ rozmiar stosu, jeśli program pobiera komunikaty przepełnienia stosu.  
  
 Można też ustawić rozmiar stosu:  
  
-   Przy użyciu **/STACK** — opcja konsolidatora. Aby uzyskać więcej informacji, zobacz [/STACK](../../build/reference/stack.md).  
  
-   Za pomocą polecenia EDITBIN plik .exe. Aby uzyskać więcej informacji, zobacz [odwołanie EDITBIN](../../build/reference/editbin-reference.md).  
  
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