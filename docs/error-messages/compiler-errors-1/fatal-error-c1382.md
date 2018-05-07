---
title: Błąd krytyczny C1382 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07c6af1209faface96585224cbd08b4e35101478
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1382"></a>Błąd krytyczny C1382
Plik PCH "file" został przebudowany od "obj" został wygenerowany. Przebuduj ten obiekt  
  
 Korzystając z [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto pliku .pch, która jest nowsza niż .obj CIL, wskazujące do niego. Informacje zawarte w pliku obj. CIL jest nieaktualny. Ponownie utworzyć obiekt.  
  
 C1382 może również wystąpić w przypadku kompilacji z **/Yc**, ale również przekazać wielu plików kodu w kompilatorze.  Aby rozwiązać, nie należy używać **/Yc** podczas przekazywania wielu plików kodu w kompilatorze.  Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md).