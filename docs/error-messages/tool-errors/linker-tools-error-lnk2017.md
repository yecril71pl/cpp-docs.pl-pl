---
title: Błąd narzędzi konsolidatora LNK2017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095423b5f2d86cef309ed4316ff72d195b11eb26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313075"
---
# <a name="linker-tools-error-lnk2017"></a>Błąd narzędzi konsolidatora LNK2017
Przeniesienie "symbol" do "segmentu" Nieprawidłowa bez: no  
  
 Próbujesz utworzyć 64-bitowy obraz z 32-bitowych adresów. W tym celu należy:  
  
-   Użyj adresu obciążenia stały.  
  
-   Ograniczanie obrazu do 3 GB.  
  
-   Określ [: No](../../build/reference/largeaddressaware-handle-large-addresses.md).