---
title: Błąd kompilatora zasobów RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 4d298cdd9d96c55f283ce7f0e2ba04dd664941f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584616"
---
# <a name="resource-compiler-error-rw2001"></a>Błąd kompilatora zasobów RW2001

Nieprawidłową dyrektywę w wstępnie przetworzony plik RC

Plik RC zawiera **#pragma** dyrektywy.

Użyj **#ifndef** dyrektywy preprocesora, za pomocą **RC_INVOKED** stałej, że kompilator zasobów definiuje podczas przetwarzania pliku dołączanego. Miejsce **#pragma** dyrektywy wewnątrz bloku kodu, który nie jest przetwarzane, gdy **RC_INVOKED** stała jest zdefiniowana. Kod w bloku jest przetwarzany tylko przez kompilator C/C++, a nie przez kompilator zasobów. Następujący przykładowy kod przedstawia tej techniki:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** dyrektywy preprocesora nie ma znaczenia w. Plik RC. **#Include** dyrektywy preprocesora jest używany często w. Plik RC, aby uwzględnić plik nagłówka (plik nagłówka niestandardowego na podstawie projektu lub pliku standardowy nagłówek dostarczonego przez firmę Microsoft przy użyciu jednego z produktów). Niektóre z nich obejmują pliki zawierają **#pragma** dyrektywy. Ponieważ plik nagłówkowy może zawierać jeden lub więcej inne pliki nagłówkowe, plik który zawiera naruszeń **#pragma** dyrektywy może nie być od razu widoczne.

**#Ifndef RC_INVOKED** technika można sterować tym pliki nagłówków w plikach nagłówkowych opartego na projektach.