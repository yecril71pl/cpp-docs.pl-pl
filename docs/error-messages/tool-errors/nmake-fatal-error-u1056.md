---
title: Błąd krytyczny NMAKE U1056 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316559"
---
# <a name="nmake-fatal-error-u1056"></a>Błąd krytyczny NMAKE U1056
Nie można znaleźć procesora poleceń  
  
 Procesor poleceń nie znajdowała się w ścieżce określonej w **COMSPEC** lub **ścieżki** zmiennych środowiskowych.  
  
 NMAKE używa COMMAND.COM lub CMD. EXE jako procesora poleceń, podczas wykonywania polecenia. Szuka procesora poleceń najpierw w ścieżce w **COMSPEC**. Jeśli **COMSPEC** nie istnieje, wyszukiwanie NMAKE katalogi określone w **ścieżki**.