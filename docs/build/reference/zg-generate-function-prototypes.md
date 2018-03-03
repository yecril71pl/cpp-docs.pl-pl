---
title: -ZG-(Generuj prototypy funkcji) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zg
dev_langs:
- C++
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03e42c32806bbe7142b8d4d03e2f0974eeacdf84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generuj prototypy funkcji)
Usuwane. Tworzy prototyp funkcji dla każdej funkcji zdefiniowanej w pliku źródłowym, ale nie kompiluje plik źródłowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zg  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja kompilatora nie jest już dostępne. Aplikacja została usunięta w programie Visual C++ 2015. Ta strona pozostaje dla użytkowników starszych wersji programu Visual C++.  
  
 Prototyp funkcji obejmują zwracanego typu funkcji i listy argumentów typu. Lista argumentów typu jest tworzony za pomocą typów parametrów formalnych funkcji. Wszystkie już istnieje w pliku źródłowym prototypy funkcji są ignorowane.  
  
 Lista prototypy są zapisywane do wyjścia standardowego. Aby sprawdzić, czy rzeczywistych argumentów i parametrów formalnych funkcji są zgodne, przydatne mogą być tej listy. Listy można zapisywać przez przekierowywanie standardowe dane wyjściowe do pliku. Następnie można użyć **#include** Aby listę prototypy funkcji część pliku źródłowego. To powoduje, że kompilator sprawdza typ argumentu.  
  
 Jeśli używasz **/Zg** opcja i program zawiera formalnych parametrów, które mają struktury, wyliczenia, lub typu Unii (lub wskaźniki do takich typów), deklaracja każdego struktury, wyliczenia lub typu Unii musi mieć tag (nazwa). W poniższym przykładzie jest nazwa tagu `MyStruct`.  
  
```C  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 **/Zg** opcja została uznana za przestarzałą w programie Visual Studio 2005 i został usunięty w programie Visual Studio 2015. Kompilator Visual C++ usunięto obsługę dla starszych, stylu języka C kodu. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
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