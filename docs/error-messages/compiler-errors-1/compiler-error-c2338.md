---
title: "C2338 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0171654bde5b056a7e6695ea5fbbe84edb62f83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2338"></a>C2338 błąd kompilatora  
  
> *Komunikat o błędzie*  
  
Przyczyną tego błędu `static_assert` wystąpił błąd podczas kompilacji. Komunikat jest dostarczana przez `static_assert` parametrów.   
  
Ten komunikat o błędzie może być również generowany przez dostawców zewnętrznych do kompilatora. W większości przypadków te błędy są zgłaszane przez dostawcę atrybut biblioteki DLL, takich jak ATLPROV. Niektóre typowe formularze tego komunikatu, obejmują:

> "*atrybutu*" dostawcy atrybutu Atl: Błąd biblioteki ATL*numer* *wiadomości*  
  
> Nieprawidłowe użycie atrybutu "*atrybutu*"
  
> "*użycia*": nieprawidłowy format atrybutu "użycie"  
  
Te błędy są często jest nieodwracalny i następuje błąd krytyczny kompilatora.  
  
Aby rozwiązać te problemy, popraw użycie atrybutu. Na przykład w niektórych przypadkach parametrów atrybutu musi być zadeklarowana przed ich użyciem. Jeśli zostanie podany numer błędu ATL, zajrzyj do dokumentacji dla tego błędu, aby uzyskać bardziej szczegółowe informacje.  
