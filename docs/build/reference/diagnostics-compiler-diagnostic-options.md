---
title: -diagnostyki (opcje kompilatora diagnostycznych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d874e26a922a7f9cce7223b574d525d37733598
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (opcje kompilatora diagnostycznych)  
  
Użyj **/diagnostics** opcję kompilatora, aby określić wyświetlanie informacji o lokalizacji błędu i ostrzeżenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>Uwagi  
**/Diagnostics** — opcja kompilatora formanty wyświetlają błędu i ostrzeżenia.  
  
**/Diagnostics:classic** jest opcja domyślna, która tylko numer wiersza, gdzie znaleziono problem.  
  
**/Diagnostics:column** opcja obejmuje również kolumny, w którym znaleziono problem. Może to pomóc w identyfikacji konstrukcji języka lub znak, który jest przyczyną problemu.  
  
**/Diagnostics:caret** opcja zawiera kolumny, których problem został znaleziony i umieszcza daszek (^) w lokalizacji w wierszu kodu, w których wykryto problem.  
  
Należy pamiętać, że w niektórych przypadkach, kompilator nie wykryje problem, na którym wystąpił. Na przykład brakuje średnika mogą nie być wykrywane dopóki napotkano innych, nieoczekiwany symboli. Kolumna jest zgłaszany i karetkę jest umieszczona na których kompilator wykryć, czy element jest nieprawidłowa, która nie jest zawsze których należy wprowadzić poprawny.  
  
**/Diagnostics** opcja jest dostępna w programie Visual Studio 2017 r.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt w **strony właściwości** okno dialogowe.   
  
2. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **ogólne** strony właściwości.  
  
3. Formant listy rozwijanej w **Format diagnostyki** pola, aby wybrać diagnostyki wyświetlaj opcji. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)