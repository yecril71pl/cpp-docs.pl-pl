---
title: "-HIGHENTROPYVA (Obsługa 64-bitowych ASLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 059f6169cafc48fc67587ae2f5827966269e6ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Adres 64-bitowej obsługi ASLR)
Określa, że obrazu wykonywalnego obsługuje randomizacji układu przestrzeni adresowej 64-bitowych wysokiej entropii (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie/highentropyva znajduje się na 64-bitowych obrazów wykonywalnych. Nie ma zastosowania do obrazy wykonywalne 32-bitowych. Aby włączyć tę opcję, /DYNAMICBASE musi być na.  
  
 / HIGHENTROPYVA modyfikuje nagłówka pliku dll lub plik .exe, aby wskazać, czy obsługiwane jest ASLR z 64-bitowych adresów. Gdy ta opcja jest ustawiona na plik wykonywalny i wszystkie moduły, w których zależy, systemu operacyjnego, który obsługuje 64-bitowych ASLR można rebase segmenty obrazu wykonywalnego w czasie ładowania przy użyciu losowego adresów w 64-bitowych wirtualnej przestrzeni adresowej. Ta przestrzeń adresowa dużych sprawia, że utrudnia osobie atakującej odgadnąć lokalizacji obszaru pamięci.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **wiersza polecenia** strony właściwości.  
  
5.  W **dodatkowe opcje**, wprowadź `/HIGHENTROPYVA` lub `/HIGHENTROPYVA:NO`.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)