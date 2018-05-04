---
title: -J (domyślny typ unsigned char) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93172296b0e2e6d54dc428ffc62812ad979b160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Domyślny typ char nie jest podpisany)
Zmienia domyślny `char` typu z `signed char` do `unsigned char`i `char` typu jest rozszerzony zero, gdy zostanie rozszerzone do `int` typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/J  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `char` wartość jest jawnie zadeklarowana jako `signed`, **/J** opcja nie dotyczy, a wartość jest znakiem, gdy zostanie rozszerzone do `int` typu.  
  
 **/J** opcja definiuje `_CHAR_UNSIGNED`, który jest używany z `#ifndef` w pliku Limits.h — można określić domyślnego `char` typu.  
  
 ANSI C i C++ nie wymagają określonej implementacji `char` typu. Ta opcja jest przydatna podczas pracy z danymi znaków, które po pewnym czasie przekształcania w innym języku niż angielski.  
  
> [!NOTE]
>  Jeśli używasz tej opcji kompilatora z ATL/MFC, może być wygenerowany błąd. Mimo że można wyłączyć ten błąd, definiując `_ATL_ALLOW_CHAR_UNSIGNED`, to rozwiązanie nie jest obsługiwana i może nie zawsze działać.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  W projekcie **strony właściwości** okno dialogowe, w lewym okienku w obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** , a następnie wybierz **wiersza polecenia**.  
  
3.  W **dodatkowe opcje** okienka, określ **/J** — opcja kompilatora.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)