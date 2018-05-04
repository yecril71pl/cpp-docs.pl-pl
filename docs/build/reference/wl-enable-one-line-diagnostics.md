---
title: -WL (Włącz diagnostykę) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58a6b41e66f7ec37ad02747edb8331049b9baef5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Włącz diagnostykę w trybie on-line)
Dołącza dodatkowe informacje do błąd lub ostrzeżenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
/WL  
```  
  
## <a name="remarks"></a>Uwagi  
 Błędów i ostrzeżeń kompilatora C++ może następować dodatkowe informacje, które pojawia się domyślnie w nowym wierszu. Podczas kompilowania z wiersza polecenia, wiersz dodatkowych informacji, można dołączyć do błąd lub ostrzeżenie. Może to być pożądane, jeśli przechwytywania danych wyjściowych kompilacji do pliku dziennika, a następnie przetworzyć tego dziennika, aby znaleźć wszystkie błędy i ostrzeżenia. Średnik musi upłynąć błąd lub ostrzeżenie z dodatkowych wiersza.  
  
 Nie wszystkie błędach i komunikaty ostrzegawcze ma wiersz dodatkowych informacji. Następujący kod zostanie wygenerowany błąd, który ma linia dodatkowych informacji. będzie można sprawdzić efekt, korzystając z **/WL**.  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
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