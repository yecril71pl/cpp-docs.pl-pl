---
title: Zmiana symbolu lub nazwy symbolu (ID) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing
dev_langs: C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 300c83a256e2a60ce9f7605093a2016f2d322785
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Zmiana symbolu lub nazwy symbolu (ID)
Podczas tworzenia nowego zasobu lub obiektu zasobów, środowisko projektowe przypisuje go domyślną nazwę symbolu, na przykład IDD_DIALOG1. Można użyć [okna właściwości](/visualstudio/ide/reference/properties-window) zmienić domyślną nazwę symbolu lub zmienić nazwę symbolu, wszystkie już skojarzony z zasobem.  
  
### <a name="to-change-a-resources-symbol-name"></a>Aby zmienić nazwę symbolu zasobu  
  
1.  W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **właściwości** okna, wpisz nową nazwę symbolu lub wybierz z listy istniejących symboli w **identyfikator** pole.  
  
     Jeśli wpiszesz nazwę symbolu, zostanie automatycznie przypisany wartość.  
  
 Można użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) zmiana nazw symboli nie jest aktualnie przypisana do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)   
 [Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)