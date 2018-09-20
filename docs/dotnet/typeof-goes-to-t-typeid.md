---
title: TypeOf operatorem T::TypeID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4433061fceef455685b6588c81c8c2e434253433
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374682"
---
# <a name="typeof-goes-to-ttypeid"></a>Operator typeof został zastąpiony operatorem T::typeid

`typeof` Operator używany w zarządzanych rozszerzeń dla C++ ma zostać supplanted przez `typeid` — słowo kluczowe w języku Visual C++.

W zarządzanych rozszerzeń `__typeof()` operator zwraca skojarzonego `Type*` obiektu, kiedy jest przekazywana nazwa typu zarządzanego. Na przykład:

```
// Creates and initializes a new Array instance.
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

W nowej składni `__typeof` został zastąpiony w innej formie `typeid` zwracającego `Type^` gdy określono typu zarządzanego.

```
// Creates and initializes a new Array instance.
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

## <a name="see-also"></a>Zobacz też

[Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[TypeID](../windows/typeid-cpp-component-extensions.md)