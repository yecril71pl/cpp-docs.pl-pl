---
title: Kompilatora (poziom 4) ostrzeżenie C4057 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3217ccb0a96fbe02e152ff82dedeb7e8e54b89ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292282"
---
# <a name="compiler-warning-level-4-c4057"></a>Kompilator C4057 ostrzegawcze (poziom 4)
"operator": operator pośredni "identifier1" do nieco innych typów podstawowych z "identifier2"  
  
 Wyrażenia wskaźników dwa odwoływać się do innych typów podstawowych. Wyrażenia są używane bez użycia konwersji.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Łączenie typów znakiem i bez znaku.  
  
2.  Mieszanie **krótki** i **długi** typów.