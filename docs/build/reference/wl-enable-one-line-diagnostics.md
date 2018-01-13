---
title: "-WL (Włącz diagnostykę) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /wl
dev_langs: C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48ba6ab05ac596c98c4fa5a95971735c62267a35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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