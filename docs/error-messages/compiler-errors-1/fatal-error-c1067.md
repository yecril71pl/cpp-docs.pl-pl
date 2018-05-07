---
title: Błąd krytyczny C1067 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ac7084e92f7f2ed496a4c1572e94a4fa46862f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067
ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu  
  
 Ten błąd może wystąpić, jeśli symbol ma nazwę ozdobione przekraczającej 247 znaków.  Aby rozwiązać, Skróć nazwę symbolu.  
  
 Gdy kompilator generuje informacje o debugowaniu, emituje rekordów typu do definiowania typów Napotkano w kodzie źródłowym.  Rejestruje typ zawierają na przykład struktury proste i listy argumentów funkcji.  Niektóre z tych rekordów typu może być dużych list.  
  
 Istnieje limit 64 KB rozmiaru dowolnego typu rekordu.  Jeśli zostanie przekroczony limit 64K ten błąd zostanie przeprowadzona.  
  
 C1067 może również wystąpić, jeśli istnieje wiele symboli o długich nazwach lub jeśli klasy, struktury lub związku ma zbyt wiele elementów członkowskich.