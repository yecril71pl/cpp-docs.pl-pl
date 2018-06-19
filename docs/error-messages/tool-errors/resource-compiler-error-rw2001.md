---
title: Błąd kompilatora zasobów RW2001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 077260b615d0a5adf32278d8857df5b8f74b7e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321103"
---
# <a name="resource-compiler-error-rw2001"></a>Błąd kompilatora zasobów RW2001
Nieprawidłowe dyrektywy wstępnie przetworzonych plików RC  
  
 Plik RC zawiera **#pragma** dyrektywy.  
  
 Użyj **#ifndef** dyrektywy preprocesora z **RC_INVOKED** stałej, że kompilator zasobów definiuje podczas przetwarzania plików dołączanych. Miejsce **#pragma** dyrektywy wewnątrz bloku kodu, który nie jest przetwarzane, gdy **RC_INVOKED** stała jest zdefiniowany. Kod w bloku jest przetwarzany tylko przez kompilator C/C++, a nie przez kompilator zasobów. Następujący przykładowy kod przedstawia tej techniki:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma** dyrektywy preprocesora nie ma znaczenia. Plik RC. **#Include** dyrektywy preprocesora jest używany często w. RC pliku, aby uwzględnić plik nagłówka (plik projektu na podstawie niestandardowy nagłówek lub pliku nagłówka standardowe dostarczane przez firmę Microsoft z jednego z jego produktów). Niektóre z nich zawierają pliki zawierają **#pragma** dyrektywy. Ponieważ plik nagłówka może zawierać jeden lub więcej inne pliki nagłówków, pliku, który zawiera naruszeń **#pragma** dyrektywy może nie być od razu widoczne.  
  
 **#Ifndef RC_INVOKED** technika można sterować tym pliki nagłówkowe w plikach projektu na podstawie nagłówka.