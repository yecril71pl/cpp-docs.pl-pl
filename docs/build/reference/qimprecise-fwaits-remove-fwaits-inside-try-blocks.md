---
title: "-Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qimprecise_fwaits
dev_langs: C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aa09590e1ede80107a085c03528b4c9089885bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Usuwanie fwaits wewnątrz bloków Try)
Usuwa `fwait` polecenia wewnętrzne `try` blokuje, korzystając z [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md) — opcja kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qimprecise_fwaits  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja nie ma efektu Jeśli **/FP: except** również nie określono. Jeśli określisz **/FP: except** opcja, kompilator powoduje wstawienie `fwait` polecenia wokół każdego wiersza kodu w `try` bloku. W ten sposób kompilator może wskazywać określonego wiersza kodu, który spowoduje utworzenie Wystąpił wyjątek. **/ Qimprecise_fwaits** usuwa wewnętrzny `fwait` instrukcje, pozostawiając tylko czeka wokół `try` bloku. Poprawia to wydajność, ale kompilator tylko będą mogli powiedzieć, które `try` wyjątek nie wiersza, który powoduje, że blok.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)