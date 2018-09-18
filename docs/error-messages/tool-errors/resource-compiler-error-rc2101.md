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
ms.openlocfilehash: 196806e6d2767c889ae96d239af69113c542ba6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034762"
---
# <a name="resource-compiler-error-rc2101"></a>Błąd kompilatora zasobów RC2101

Nieprawidłową dyrektywę w wstępnie przetworzony plik RC

Zawiera kompilator zasobów **#pragma** dyrektywy.

Użyj **#ifndef** dyrektywy preprocesora z stałą RC_INVOKED, że kompilator zasobów definiuje podczas przetwarzania pliku dołączanego. Miejsce **#pragma** dyrektywy wewnątrz bloku kodu, która nie została przetworzona, gdy stała RC_INVOKED jest zdefiniowany. Kod w bloku jest przetwarzany tylko przez kompilator C/C++, a nie przez kompilator zasobów. Następujący przykładowy kod przedstawia tej techniki:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** dyrektywy preprocesora nie ma znaczenia w. Plik RC. **#Include** dyrektywy preprocesora jest używany często w. Plik RC, aby uwzględnić plik nagłówka (plik nagłówka niestandardowego na podstawie projektu lub pliku standardowy nagłówek dostarczonego przez firmę Microsoft przy użyciu jednego z produktów). Niektóre z nich obejmują pliki zawierają **#pragma** dyrektywy. Ponieważ plik nagłówkowy może zawierać jeden lub więcej inne pliki nagłówkowe, plik który zawiera naruszeń **#pragma** dyrektywy może nie być od razu widoczne.

**#Ifndef** technika RC_INVOKED można sterować tym pliki nagłówków w plikach nagłówkowych opartego na projektach.