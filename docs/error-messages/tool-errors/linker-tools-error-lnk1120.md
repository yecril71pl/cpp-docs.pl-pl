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
ms.openlocfilehash: f1d2a55d683e9c8b9d6a0da2b3e5fa78d5a39933
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725572"
---
# <a name="linker-tools-error-lnk1120"></a>Błąd narzędzi konsolidatora LNK1120

> *Liczba* nierozpoznanych elementów zewnętrznych  
  
Błąd LNK1120 liczności (*numer*) błędów nierozpoznany symbol zewnętrzny dla tej operacji łączenia. Większość nierozpoznanych symboli zewnętrznych błędy są zgłaszane indywidualnie przez [błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) i [błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), które poprzedzają ten komunikat o błędzie, jeden raz dla każdego nierozpoznany zewnętrzny symbol błędu.  
  
Aby naprawić ten błąd, należy rozwiązać wszystkie inne nierozwiązane błędy zewnętrznych lub inne błędy konsolidatora, które należy poprzedzić go w danych wyjściowych kompilacji. Ten błąd nie jest zgłaszany, kiedy pozostają żadne nierozwiązane błędy zewnętrznych.  
