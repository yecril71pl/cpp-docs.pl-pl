---
title: -await (Włącz obsługę procedura wspólna) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78a62195ca28be49ed8c00dacacce003281699f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="await-enable-coroutine-support"></a>/ await (Włącz obsługę procedura wspólna)  
  
Użyj **/ await** opcję kompilatora, aby włączyć obsługę kompilatora koprocedurach.  
  
## <a name="syntax"></a>Składnia  
  
> / await  
  
## <a name="remarks"></a>Uwagi  
  
**/ Await** — opcja kompilatora umożliwia obsługę kompilatora C++ w procedurach wspólnych i słowa kluczowe **co_await**, **co_yield**, i **co_return**. Ta opcja jest domyślnie wyłączona. Informacje na temat obsługi dla koprocedury w programie Visual Studio, zobacz [blogu zespołu programu Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Aby uzyskać więcej informacji o procedurach wspólnych propozycji standardowe, zobacz [N4628 pracy w wersji próbnej, specyfikacji technicznej rozszerzenia C++ dla Koprocedury](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).  

**/ Await** opcja jest dostępne począwszy od wersji programu Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt w **strony właściwości** okno dialogowe.   
  
2. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **wiersza polecenia** strony właściwości.  
  
3. Wprowadź **/ await** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
  
[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)