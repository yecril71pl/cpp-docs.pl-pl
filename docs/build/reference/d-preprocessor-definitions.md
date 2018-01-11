---
title: -D (definicje preprocesora) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
dev_langs: C++
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 08812cdd0a4ffb27b387cce8cfb26e72ef80770a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="d-preprocessor-definitions"></a>/D (Definicje preprocesora)
Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć tego symbolu razem z `#if` lub `#ifdef` warunkowo skompilować kod źródłowy. Definicji symbolu pozostaje, dopóki zostało ponownie zdefiniowane w kodzie, lub jest niezdefiniowana w kodzie przez `#undef` dyrektywy.  
  
 **/D** ma ten sam efekt co `#define` dyrektywy na początku pliku kodu źródłowego, z wyjątkiem **/D** usuwa znaki cudzysłowu w wierszu polecenia i `#define` je zachowuje.  
  
 Domyślnie wartość skojarzona z symbolem to 1. Na przykład **/D** `name` jest odpowiednikiem **/D**`name`**= 1**. W tym przykładzie na końcu tego artykułu, definicji **testu** jest wyświetlany na drukowanie `1`.  
  
 Kompilowanie przy użyciu **/D** `name`  **=**  powoduje, że symbol niezawierające skojarzone wartości. Mimo że nadal można używać symbolu, aby warunkowo skompilować kod, szacuje się on na wartość nothing. W tym przykładzie skompilować przy użyciu **/DTEST =**, wystąpi błąd. To zachowanie jest podobny do stosowania `#define` z lub bez wartości.  
  
 To polecenie definiuje symbol DEBUG w TEST.c:  
  
 **CL /DDEBUG TESTU. C**  
  
 To polecenie usuwa wszystkie wystąpienia słowa kluczowego `__far` w TEST.c:  
  
 **CL /D__far = TEST. C**  
  
 **CL** zmienna środowiskowa nie można ustawić na ciąg, który zawiera znaku równości. Aby użyć **/D** razem z **CL** środowiska zmiennej, należy określić znak liczby zamiast znaku równości:  
  
```  
SET CL=/DTEST#0  
```  
  
 Podczas definiowania symbolu przetwarzania wstępnego w wierszu polecenia, należy wziąć pod uwagę reguły analizy składni zarówno kompilatora, jak i powłoki. Na przykład, aby zdefiniować w programie symbol wstępnego przetwarzania znaku procenta (%), określ dwa znaki procenta (%%) w wierszu polecenia: Jeśli określisz tylko jeden, zostanie wygenerowany błąd analizy składni.  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku po lewej stronie wybierz **właściwości konfiguracji**, **C/C++**, **preprocesora**.  
  
3.  W prawym okienku w prawej kolumnie **definicje preprocesora** właściwości, otwórz menu rozwijane i wybierz polecenie **Edytuj**.  
  
4.  W **definicje preprocesora** okno dialogowe Dodawanie (każde w oddzielnym wierszu), zmodyfikować lub usunąć co najmniej jedną definicję. Wybierz **OK** Aby zapisać zmiany.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_D_compiler_option.cpp  
// compile with: /DTEST  
#include <stdio.h>  
  
int main( )  
{  
    #ifdef TEST  
        printf_s("TEST defined %d\n", TEST);  
    #else  
        printf_s("TEST not defined\n");  
    #endif  
}  
```  
  
```Output  
TEST defined 1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ U, /u (Usuń definicje symboli)](../../build/reference/u-u-undefine-symbols.md)   
 [#undef — dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)