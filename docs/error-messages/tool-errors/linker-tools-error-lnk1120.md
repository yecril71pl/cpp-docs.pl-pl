---
title: Błąd narzędzi konsolidatora LNK1120 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fab2b937f8bf941219c678c638e9757903ee7698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298515"
---
# <a name="linker-tools-error-lnk1120"></a>Błąd narzędzi konsolidatora LNK1120
*numer* nierozpoznane obiektów zewnętrznych  
  
Błąd LNK1120 liczności (*numer*) błędów nierozpoznany zewnętrzny symbol dla tej operacji łącza. Większość nierozpoznane osobno zostały zgłoszone błędy zewnętrzny symbol [błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) i [błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), który poprzedzać ten komunikat o błędzie, tylko jeden raz dla każdego nierozwiązane zewnętrzne Błąd symbolu.  
  
Aby naprawić ten błąd, należy rozwiązać wszystkie inne nierozwiązane błędy zewnętrznych lub inne błędy konsolidatora, które należy poprzedzić go w danych wyjściowych kompilacji. Ten błąd nie jest zgłaszany, kiedy pozostają bez nierozwiązane błędów zewnętrznych.  
