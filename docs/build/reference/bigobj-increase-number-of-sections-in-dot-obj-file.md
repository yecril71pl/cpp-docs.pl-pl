---
title: "-bigobj (Zwiększ liczbę sekcji w. Plik obj) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /bigobj
dev_langs: C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384ec0de9e5cb1b3172b980bf7f412abe759ff91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zwiększ ilość sekcji w pliku .Obj)
**/ bigobj** zwiększa liczbę sekcji zawierających pliku obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie plik obiektu może przechowywać maksymalnie 65 536 (2 ^ 16) mogą być adresowane sekcje. Dotyczy to niezależnie od tego, który określono platformy docelowej. **/ bigobj** zwiększa wydajność adres do 4 294 967 296 (2 ^ 32).  
  
 Większość modułów nigdy nie zostanie wygenerowany plik .obj, który zawiera więcej niż 65 536 sekcje. Kod wygenerowany przez komputer lub kod, który intensywnie korzysta z biblioteki szablonów może wymagać plików .obj, które mogą zawierać więcej sekcji. **/ bigobj** jest włączona domyślnie w przypadku projektów Sklepu Windows, ponieważ kod XAML wygenerowane maszynowo zawiera dużą liczbę nagłówków. Jeśli wyłączysz tę opcję na projektem aplikacji ze Sklepu Windows najprawdopodobniej będzie wystąpi błąd kompilatora C1128.  
  
 Linkery, które zostały wydane przed Visual C++ 2005 nie można odczytać plików .obj, które zostały utworzone z **/bigobj**.  
  
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