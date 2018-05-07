---
title: Błąd kompilatora zasobów RC2101 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2101
dev_langs:
- C++
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b07f6211e1cc36bd471b04126e724e42eb610641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2101"></a>Błąd kompilatora zasobów RC2101
Nieprawidłowe dyrektywy wstępnie przetworzonych plików RC  
  
 Plik kompilator zasobów zawiera **#pragma** dyrektywy.  
  
 Użyj **#ifndef** dyrektywy preprocesora z stałą RC_INVOKED, że kompilator zasobów definiuje podczas przetwarzania plików dołączanych. Miejsce **#pragma** dyrektywy wewnątrz bloku kodu, która nie została przetworzona, gdy definiowany jest stała RC_INVOKED. Kod w bloku jest przetwarzany tylko przez kompilator C/C++, a nie przez kompilator zasobów. Następujący przykładowy kod przedstawia tej techniki:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **#Pragma** dyrektywy preprocesora nie ma znaczenia. Plik RC. **#Include** dyrektywy preprocesora jest używany często w. RC pliku, aby uwzględnić plik nagłówka (plik projektu na podstawie niestandardowy nagłówek lub pliku nagłówka standardowe dostarczane przez firmę Microsoft z jednego z jego produktów). Niektóre z nich zawierają pliki zawierają **#pragma** dyrektywy. Ponieważ plik nagłówka może zawierać jeden lub więcej inne pliki nagłówków, pliku, który zawiera naruszeń **#pragma** dyrektywy może nie być od razu widoczne.  
  
 **#Ifndef** technika RC_INVOKED można sterować tym pliki nagłówkowe w plikach projektu na podstawie nagłówka.