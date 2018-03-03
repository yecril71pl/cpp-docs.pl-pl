---
title: "-Gs (Kontroluj wywołania sprawdzania stosu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /GS
dev_langs:
- C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff02465b4e1b1a727a2367c8d5e038f30854ecc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (Kontroluj wywołania sprawdzania stosu)
Sondy stosu kontrolki.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>Argumenty  
 `size`  
 (Opcjonalnie) Liczba bajtów, które zmienne lokalne mogą zajmować przed sondy stosu jest inicjowana. Jeśli **/GS** określono opcję bez `size` argumentu, jest taki sam jak określenie **/Gs0**,  
  
## <a name="remarks"></a>Uwagi  
 Sondy stosu jest sekwencją kodu, który zostanie wstawiona do każdego wywołania funkcji. Po zainicjowaniu, sondy stosu osiągnie benignly do pamięci przez ilość miejsca, która jest wymagana do przechowywania funkcji zmiennych lokalnych.  
  
 Jeśli funkcja wymaga więcej niż `size` bajtów stosu miejsce dla zmiennych lokalnych, jego sondy stosu jest inicjowana. Domyślnie kompilator generuje kod, który inicjuje sondy stosu, gdy funkcja wymaga więcej niż jedną stronę miejsca na stosie. Jest to równoważne opcji kompilatora **/Gs4096** dla x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]i platformy ARM. Ta wartość umożliwia aplikacji i systemu Windows, Menedżer pamięci zwiększyć ilość pamięci przydzielonej do stosu program dynamicznie w czasie wykonywania.  
  
> [!NOTE]
>  Wartość domyślna **/Gs4096** umożliwia stosu program aplikacji dla systemu Windows zwiększa się poprawnie w czasie wykonywania. Zaleca się, że należy zmieniać wartości domyślnej znając dokładnie Dlaczego należy ją zmienić.  
  
 Niektóre programy — na przykład sterowniki urządzeń wirtualnych — nie wymagają tego domyślnego mechanizmu wzrostu stosu. W takich przypadkach sondy stosu nie są niezbędne i zatrzymaniu kompilatora z generować je przez ustawienie `size` na wartość większą niż dowolnej funkcji wymaga lokalnego magazynu zmiennej. Nie może być spacji między **/GS** i `size`.  
  
 **/ Gs0** aktywuje sondy stosu dla każdego wywołania funkcji, który wymaga magazynu dla zmiennych lokalnych. Może to mieć negatywny wpływ na wydajność.  
  
 Sondy stosu lub wyłącz można włączyć za pomocą [check_stack —](../../preprocessor/check-stack.md). **/ GS** i `check_stack` pragma nie mają wpływu na standardowe procedury biblioteki C; wpływają tylko funkcje, które można skompilować.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)