---
title: -constexpr (oceny specyfikatora constexpr kontroli) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /constexpr
- -constexpr
dev_langs:
- C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f83f1d9a505ebc4c05ce4e367bb1e978d6a14b78
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (oceny specyfikatora constexpr sterowania)  
  
Użyj **/constexpr** — opcje kompilatora sterowania parametrami dla `constexpr` oceny w czasie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
> /constexpr:DEPTH*N*  
> /constexpr:backtrace*N*  
> Steps*N*  
  
## <a name="arguments"></a>Argumenty  
  
**głębokość *** N*  
Ogranicz głębokość cykliczne `constexpr` na wywołania funkcji *N* poziomów. Wartość domyślna to 512.  
  
**backtrace *** N*  
Pokaż maksymalnie *N* `constexpr` oceny w diagnostyce. Wartość domyślna to 10.  
  
**kroki *** N*  
Przerwanie `constexpr` szacowania po *N* czynności. Wartość domyślna to 100 000.  
  
## <a name="remarks"></a>Uwagi  
  
**/Constexpr** kompilatora opcje umożliwiają kontrolowanie oceny kompilacji `constexpr` wyrażenia. Kroki oceny, poziom rekursji i głębokość backtrace są kontrolowane aby uniemożliwić kompilatorowi wydatków zbyt dużo czasu na `constexpr` oceny. Aby uzyskać więcej informacji na temat `constexpr` element języka, zobacz [constexpr (C++)](../../cpp/constexpr-cpp.md).  

**/Constexpr** opcje są dostępne począwszy od wersji programu Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt w **strony właściwości** okno dialogowe.   
  
2. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **wiersza polecenia** strony właściwości.  
  
3. Wprowadź wszelkie **/constexpr** opcje kompilatora w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
  
[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)