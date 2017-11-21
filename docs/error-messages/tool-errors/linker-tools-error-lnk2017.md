---
title: "Błąd narzędzi konsolidatora LNK2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2017
dev_langs: C++
helpviewer_keywords: LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f1b588abe7bb222751506e21d90b4b8596b381f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2017"></a>Błąd narzędzi konsolidatora LNK2017
Przeniesienie "symbol" do "segmentu" Nieprawidłowa bez: no  
  
 Próbujesz utworzyć 64-bitowy obraz z 32-bitowych adresów. W tym celu należy:  
  
-   Użyj adresu obciążenia stały.  
  
-   Ograniczanie obrazu do 3 GB.  
  
-   Określ [: No](../../build/reference/largeaddressaware-handle-large-addresses.md).