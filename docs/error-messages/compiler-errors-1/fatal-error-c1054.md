---
title: Błąd krytyczny C1054 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9daac4944c57dbf08fe0ebcbc95993a97838585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198901"
---
# <a name="fatal-error-c1054"></a>Błąd krytyczny C1054
ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko  
  
 Kod przekracza limit zagnieżdżania inicjatory (w zależności od kombinację typów inicjowany poziomy 10 – 15).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Uproszczenie inicjowany, aby zmniejszyć zagnieżdżanie typów danych.  
  
2.  Inicjowanie zmiennych w osobnych instrukcji po deklaracji.