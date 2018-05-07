---
title: Błąd krytyczny NMAKE U1045 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 673b20dde7156025c6aa56c487433eebe9e77aa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045
Duplikowanie nie powiodło się: wiadomości  
  
 Polecenie wywoływane przez NMAKE nie powiodło się z powodu danego lub program. Gdy NMAKE wywołuje inny program — na przykład kompilatora lub konsolidatora — wywołanie może się nie powieść lub błąd mogą być zwrócone przez program o nazwie. Ten komunikat jest używane do zgłaszania błędu.  
  
 Aby rozwiązać ten problem, należy najpierw ustalić przyczynę błędu. Można użyć poleceń zgłoszone przez NMAKE [/N](../../build/nmake-options.md) opcję, aby sprawdzić ustawienia środowiska i Powtórz akcje wykonywane przez NMAKE w wierszu polecenia.