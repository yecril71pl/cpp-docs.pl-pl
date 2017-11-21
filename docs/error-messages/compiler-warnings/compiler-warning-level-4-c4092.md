---
title: "Kompilatora (poziom 4) ostrzeżenie C4092 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4092
dev_langs: C++
helpviewer_keywords: C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a148417b45b9c898da9c7312512b226590c7442d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4092"></a>Kompilator C4092 ostrzegawcze (poziom 4)
Zwraca "unsigned long" sizeof  
  
 Argument operacji `sizeof` operator jest bardzo duży, dlatego `sizeof` zwrócił niepodpisany **długi**. To ostrzeżenie występuje w ramach rozszerzenia Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). W obszarze Zgodność ANSI (/Za) zamiast tego zostanie obcięta wynik.