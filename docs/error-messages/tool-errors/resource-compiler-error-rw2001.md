---
title: "Błąd kompilatora zasobów RW2001 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a14cd36ab87297cf5bc0aa547bdea5ef23260e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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