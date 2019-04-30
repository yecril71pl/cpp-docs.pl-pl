---
title: Błąd kompilatora zasobów RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345287"
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