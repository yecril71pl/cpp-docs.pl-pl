---
title: "-OI-(Generuj funkcje wewnętrzne) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs: C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d0a24830dbc67466e52f3f3c488dda7ac5b4778d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Generuj funkcje wewnętrzne)
Szybsze zastępuje niektórych funkcji wywołania z wewnętrznych lub w przeciwnym razie specjalnych formy funkcji pomagających w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Oi[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Programy używające funkcji wewnętrznej są szybsze, ponieważ bez nakładów związanych z wywołania funkcji, ale może być większy z powodu dodatkowy kod utworzony.  
  
 Zobacz [wewnętrzne](../../preprocessor/intrinsic.md) Aby uzyskać więcej informacji, które ma funkcje wewnętrzne formularzy.  
  
 **/OI** jest tylko żądania do kompilatora zastąpić niektóre wywołania funkcji funkcje wewnętrzne; kompilator może wywołanie funkcji (i nie Zastąp wywołanie funkcji wewnętrznej) czy będzie zapewnia lepszą wydajność.  
  
 **x86 określonych**  
  
 Wewnętrzne funkcje liczb zmiennoprzecinkowych nie wykonywać żadnych specjalnych kontrole wartości wejściowe tak działają w ograniczonym zakresy danych wejściowych i mają różne wyjątków i warunków ograniczających niż procedury biblioteki o takiej samej nazwie. Za pomocą formularzy wewnętrzna wartość true oznacza utraty IEEE wyjątków i utratę `_matherr` i `errno` funkcjonalności; oznacza to drugie utraty zgodność ANSI. Jednak wewnętrzna formularze znacznie przyspieszyć floating point obciążający programy, a wiele programów problemy dotyczące zgodności są o niewielkiej wartości praktyczne.  
  
 Można użyć [Za](../../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora do przesłonięcia generowania true wewnętrzne opcje zmiennoprzecinkowych. W takim przypadku funkcje są generowane jako procedury biblioteki, które przekazywać argumenty bezpośrednio do liczb zmiennoprzecinkowych mikroukładu zamiast wypychanie ich na stosie programu.  
  
 **KOŃCOWY x86 określonych**  
  
 Można również użyć [wewnętrzne](../../preprocessor/intrinsic.md) można utworzyć funkcje wewnętrzne lub [— funkcja (C/C++)](../../preprocessor/function-c-cpp.md) jawnie wymusić wywołania funkcji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **optymalizacji** strony właściwości.  
  
4.  Modyfikowanie **Włącz funkcje wewnętrzne** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Funkcje wewnętrzne kompilatora](../../intrinsics/compiler-intrinsics.md)