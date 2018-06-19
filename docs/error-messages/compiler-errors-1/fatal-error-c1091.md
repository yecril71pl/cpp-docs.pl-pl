---
title: Błąd krytyczny C1091 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48c9dca72bddc844e94fb7978cb6414aa8fecf5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226224"
---
# <a name="fatal-error-c1091"></a>Błąd krytyczny C1091
ograniczenie kompilatora: ciąg przekracza "length" bajtów długości  
  
 Stałą typu string przekracza bieżący limit długości ciągów.  
  
 Można podzielić ciąg statycznych zmiennych dwie (lub więcej) i używać [strcpy_s —](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) sprzęgać wynik w ramach deklaracji lub w czasie wykonywania.