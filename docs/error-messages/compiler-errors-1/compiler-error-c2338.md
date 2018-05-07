---
title: C2338 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156074f20517c1d2e2f4fdb4ac5c54d6cf014276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
