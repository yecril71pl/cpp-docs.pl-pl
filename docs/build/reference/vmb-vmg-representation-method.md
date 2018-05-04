---
title: -vmb, - vmg (metoda reprezentacji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vmb
- /vmg
dev_langs:
- C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5263b6c7ca227a10b34c32e0b0801eeddf07b9cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (Metoda reprezentacji)
Wybierz metodę używaną do reprezentowania wskaźników do elementów członkowskich klasy kompilatora.  
  
 Użyj **/vmb** Jeśli możesz zawsze Definiowanie klasy, aby zadeklarować wskaźnika do elementu członkowskiego klasy.  
  
 Użyj **/vmg** Aby zadeklarować wskaźnika do elementu członkowskiego klasy przed zdefiniowaniem klasy. Te wymagania mogą wystąpić w przypadku definiowania elementów członkowskich w dwóch różnych klas, które odwołują się do siebie. Dla tych klas wzajemnie odwołujący się jedną klasę musi odwoływać się przed jego zdefiniowaniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
/vmb  
/vmg  
```  
  
## <a name="remarks"></a>Uwagi  
 Można również użyć [pointers_to_members](../../preprocessor/pointers-to-members.md) lub [słowa kluczowe dziedziczenia](../../cpp/inheritance-keywords.md) w kodzie do określania reprezentacja wskaźnika.  
  
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