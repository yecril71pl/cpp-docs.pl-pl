---
title: Błąd krytyczny C1045 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1045
dev_langs:
- C++
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78ff500d050fbb646dd97fc898279712fb750d9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197614"
---
# <a name="fatal-error-c1045"></a>Błąd krytyczny C1045
ograniczenie kompilatora: powiązanie konsolidacji zagnieżdżono zbyt głęboko  
  
 Zagnieżdżone externals przekracza limit kompilatora. Zagnieżdżone externals są dozwolone z typem połączenie zewnętrzne, takie jak `extern` "C++". Zmniejsz liczbę zagnieżdżonych externals, aby rozwiązać problem.