---
title: "Błąd krytyczny NMAKE U1045 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1045
dev_langs: C++
helpviewer_keywords: U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1820b33d59d7dd9b8c96c269dd65518bafb4f0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045
Duplikowanie nie powiodło się: wiadomości  
  
 Polecenie wywoływane przez NMAKE nie powiodło się z powodu danego lub program. Gdy NMAKE wywołuje inny program — na przykład kompilatora lub konsolidatora — wywołanie może się nie powieść lub błąd mogą być zwrócone przez program o nazwie. Ten komunikat jest używane do zgłaszania błędu.  
  
 Aby rozwiązać ten problem, należy najpierw ustalić przyczynę błędu. Można użyć poleceń zgłoszone przez NMAKE [/N](../../build/nmake-options.md) opcję, aby sprawdzić ustawienia środowiska i Powtórz akcje wykonywane przez NMAKE w wierszu polecenia.