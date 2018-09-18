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
ms.openlocfilehash: f401ce7c9a96cfeecf195b8872a704b8b1291939
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114985"
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