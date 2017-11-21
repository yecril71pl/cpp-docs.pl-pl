---
title: "-Zi (Pomiń domyślną nazwę biblioteki) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs: C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b0d4f865d060ceaf99a808d87574cb6d088f139
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="zl-omit-default-library-name"></a>/Zl (Pomiń domyślną nazwę biblioteki)
Pomija domyślną nazwę biblioteki środowiska uruchomieniowego C z pliku .obj. Domyślnie kompilator umieszcza nazwę biblioteki w pliku obj. przekierować konsolidator odpowiedniej biblioteki.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zl  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na domyślnej biblioteki, zobacz [biblioteki wykonawczej użyj](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 Można użyć **/Zl** skompilować pliki .obj, w których mają zostać poddane biblioteki. Chociaż pominięcie nazwę biblioteki zapisuje małej ilości miejsca dla plików .obj pojedynczego, całkowita ilość miejsca zapisany jest znaczących w bibliotece, który zawiera wiele modułów obiektu.  
  
 Ta opcja jest zaawansowana opcja. Ta opcja powoduje usunięcie niektórych Obsługa bibliotek C Runtime, które mogą być wymagane przez aplikację, co w czasie konsolidacji błędy, jeśli aplikacja jest zależna od tej obsługi. W przypadku wybrania tej opcji należy podać wymaganych składników w inny sposób.  
  
 Użyj [/nodefaultlib (Ignoruj biblioteki)](../../build/reference/nodefaultlib-ignore-libraries.md). Aby nakazać programowi konsolidator, aby zignorować biblioteki odwołuje się we wszystkich plikach .obj.  
  
 Aby uzyskać więcej informacji, zobacz [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
 Podczas kompilowania za pomocą **/Zl**, `_VC_NODEFAULTLIB` jest zdefiniowany.  Na przykład:  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **Pomiń domyślne nazwy bibliotek** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)