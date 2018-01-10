---
title: "Błąd krytyczny NMAKE U1056 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1056
dev_langs: C++
helpviewer_keywords: U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41db646e2559051c11de5265900dde8ad0a03214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1056"></a>Błąd krytyczny NMAKE U1056
Nie można znaleźć procesora poleceń  
  
 Procesor poleceń nie znajdowała się w ścieżce określonej w **COMSPEC** lub **ścieżki** zmiennych środowiskowych.  
  
 NMAKE używa COMMAND.COM lub CMD. EXE jako procesora poleceń, podczas wykonywania polecenia. Szuka procesora poleceń najpierw w ścieżce w **COMSPEC**. Jeśli **COMSPEC** nie istnieje, wyszukiwanie NMAKE katalogi określone w **ścieżki**.