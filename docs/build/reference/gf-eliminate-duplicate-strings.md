---
title: "-GF (eliminowanie ciągów zduplikowanych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
dev_langs:
- C++
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d69e892fb9487b66da4dfa2a801bab302e962af7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminowanie ciągów zduplikowanych)
Umożliwia kompilatorowi tworzenia pojedynczej kopii identycznych ciągów w obrazie programu i pamięci podczas wykonywania. Jest to optymalizacją nazywaną *buforowania ciągu* aby tworzenia mniejszymi programami.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GF  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz **/GF**, system operacyjny nie zamiana części ciągu pamięci i może być odczytany ciągów wykonaj kopię z pliku obrazu.  
  
 **/GF** pul ciągi jako tylko do odczytu. Jeśli użytkownik próbuje zmodyfikować ciągów w obszarze **/GF**, występuje błąd aplikacji.  
  
 Buforowanie ciągów umożliwia co miały jako wskaźniki wiele do wielu buforów się wiele wskaźniki do pojedynczego buforu. W poniższym kodzie `s` i `t` są inicjowane z tych samych parametrach. Buforowanie ciągów powoduje, że ich do punktu w tej samej pamięci:  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) , używane Edytuj i Kontynuuj, powoduje **/GF** opcji.  
  
> [!NOTE]
>  **/GF** — opcja kompilatora tworzy sekcję z adresowanego dla każdego unikatowego ciągu. I domyślnie pliku obiektu może zawierać do 65 536 sekcje adresowanego. Jeśli program zawiera więcej niż 65 536 ciągów, użyj [/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) opcję kompilatora, aby utworzyć więcej sekcji.  
  
 **/GF** jest w życie, kiedy [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub **/O2** jest używany.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **Włącz buforowanie Stringów** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)