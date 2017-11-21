---
title: "Ostrzeżenie LNK4206 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1227cd792065198a3cd7f7a684e51e7c87452e77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4206"></a>Ostrzeżenie LNK4206 narzędzi konsolidatora
informacje o wstępnie skompilowanym typie nie można odnaleźć; "filename" nie został skonsolidowany ani nadpisany; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania  
  
 Plik danego obiektu skompilowanego z [/Yc](../../build/reference/yc-create-precompiled-header-file.md), albo nie został określony w poleceniu łącze lub została zastąpiona.  
  
 Typowy scenariusz dla to ostrzeżenie jest podczas .obj, który został skompilowany z /Yc znajduje się w bibliotece oraz gdzie nie ma żadnych odwołań do symboli do tego .obj w kodzie.  W takim przypadku konsolidator zostanie nie używać (lub nawet) pliku obj..  W takiej sytuacji należy ponownie skompilować kod i użyć [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) dla pozostałe obiekty (obiekty, które nie są kompilowane przy użyciu /Yc).