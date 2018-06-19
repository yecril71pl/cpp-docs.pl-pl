---
title: Kompilatora (poziom 4) ostrzeżenie C4092 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca145addc16306d613817643e363ecd9c95069a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292191"
---
# <a name="compiler-warning-level-4-c4092"></a>Kompilator C4092 ostrzegawcze (poziom 4)
Zwraca "unsigned long" sizeof  
  
 Argument operacji `sizeof` operator jest bardzo duży, dlatego `sizeof` zwrócił niepodpisany **długi**. To ostrzeżenie występuje w ramach rozszerzenia Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). W obszarze Zgodność ANSI (/Za) zamiast tego zostanie obcięta wynik.