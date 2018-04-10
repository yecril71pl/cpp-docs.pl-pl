---
title: Błąd narzędzi konsolidatora LNK1120 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82fb2f290bc0aeaf8332e642c014006d38b5c97d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1120"></a>Błąd narzędzi konsolidatora LNK1120
*numer* nierozpoznane obiektów zewnętrznych  
  
Błąd LNK1120 liczności (*numer*) błędów nierozpoznany zewnętrzny symbol dla tej operacji łącza. Większość nierozpoznane osobno zostały zgłoszone błędy zewnętrzny symbol [błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) i [błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), który poprzedzać ten komunikat o błędzie, tylko jeden raz dla każdego nierozwiązane zewnętrzne Błąd symbolu.  
  
Aby naprawić ten błąd, należy rozwiązać wszystkie inne nierozwiązane błędy zewnętrznych lub inne błędy konsolidatora, które należy poprzedzić go w danych wyjściowych kompilacji. Ten błąd nie jest zgłaszany, kiedy pozostają bez nierozwiązane błędów zewnętrznych.  
