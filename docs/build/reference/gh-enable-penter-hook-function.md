---
title: "-Gh (Włącz funkcję _penter Hook) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _penter
dev_langs: C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dec38a8822bb8a330c4dccff9833780ea3a0a45d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (Włącz funkcję _penter Hook)
Powoduje, że wywołanie `_penter` funkcja na początku każdej metody lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gh  
```  
  
## <a name="remarks"></a>Uwagi  
 `_penter` Funkcja nie jest częścią żadnej biblioteki i jest maksymalnie o podanie definicji `_penter`.  
  
 Jeśli nie chcesz jawnie wywołać `_penter`, nie trzeba podać prototypu. Funkcja muszą znajdować się tak, jakby miała następujące prototypu, a i musi być wypychania zawartości wszystkich rejestrów na zapis pop zawartości bez zmian na wyjściu:  
  
```  
void __declspec(naked) _cdecl _penter( void );  
```  
  
 Ta deklaracja nie jest dostępne dla projektów 64-bitowych.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy kod, gdy skompilowano z opcją **/Gh**, pokazuje sposób `_penter` jest wywoływana dwukrotnie; raz podczas wprowadzania funkcja `main` i raz podczas wprowadzania funkcji `x`.  
  
```  
// Gh_compiler_option.cpp  
// compile with: /Gh  
// processor: x86  
#include <stdio.h>  
void x() {}  
  
int main() {  
   x();  
}  
  
extern "C" void __declspec(naked) _cdecl _penter( void ) {  
   _asm {  
      push eax  
      push ebx  
      push ecx  
      push edx  
      push ebp  
      push edi  
      push esi  
    }  
  
   printf_s("\nIn a function!");  
  
   _asm {  
      pop esi  
      pop edi  
      pop ebp  
      pop edx  
      pop ecx  
      pop ebx  
      pop eax  
      ret  
    }  
}  
```  
  
```Output  
In a function!  
In a function!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)